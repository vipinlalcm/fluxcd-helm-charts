kubeseal --fetch-cert \
--controller-name=sealed-secrets-controller \
--controller-namespace=flux-system \
> ./certificate/pub-sealed-secrets.pem

** This example is for zorgo-testing/loki-distributed **

kubectl create secret generic loki-values --dry-run=client -n kube-logging --from-file=values.yaml -o yaml > base64-values.yaml


kubeseal --scope namespace-wide --cert ./certificate/pub-sealed-secrets.pem < base64-values.yaml > sealed-secret.yaml

copy and paste the files sealed-secret.yaml in to zorgo-testing/loki-distributed directory