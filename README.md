# Kubernetes External Secrets Crds

Allows you to create CRDs for [godaddy/kubernetes-external-secrets](https://github.com/godaddy/kubernetes-external-secrets) using separate helm release. It's useful as a dependency for applications charts

## Prerequisites

* [godaddy/kubernetes-external-secrets](https://github.com/godaddy/kubernetes-external-secrets)

## Installing

```$ helm install my-release-name https://github.com/wzooff/kubernetes-external-secrets-crds/releases/download/v0.1.1/helm-chart.tgz```

## Debug

Append ```--dry-run``` to your install command to see what CRDs will be generated.

## Adding secret

Create ```your-values.yml``` file: 

```yaml
name: myapp-external
systemManager:
  data:
    foo: /alpha/beta/bar
```

You will get k8s secret:

```yaml
apiVersion: v1
data:
  foo: hashedAlphaBetaBarValue
kind: Secret
metadata:
  name: myapp-external
type: Opaque
```
