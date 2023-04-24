```bash
# Create cluster
minikube start --cpus 2 --memory 1900 --profile c0

# Flux boostrap (requires Github personal access token)
flux bootstrap github --owner=wcarlsen --repository="flux-dev" --path clusters/c0 --read-write-key --personal  --private=false

# Start "local development" with weave-gitops ()
gitops beta run ./infrastructure/clusters/c0 --skip-dashboard-install --no-session --no-bootstrap --allow-k8s-context=c0

# Any dashboard installed if --skip-dashboard-install is removed wont be garbage collected
```
