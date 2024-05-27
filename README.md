# Radicale deployment on Kubernetes

This repository serves as a base for deploying Radicale on Kubernetes,
using just `kubectl` and the built-in
[`kustomize`](https://kubectl.docs.kubernetes.io/installation/kustomize/).

You should create your own `kustomization.yaml`, importing this repository
as a resource. `kustomize` allows you to tailor it to your own use case in
a template-free manner.

This also sets up a Traefik IngressRoute for Radicale using the `websecure` endpoint.


## Quickstart

It's very likely that you'll need to customize the deployment to your own use case.
At the very least, you should change the default account and password (test/test).

To test this deployment as-is you just need to create a `kustomization.yaml` file:

```
cat <<EOF >kustomization.yaml
resources:
- https://github.com/rmsc/radicale-kubernetes.git
EOF

```

You can then examine the created resources with the following command:

```
kubectl kustomize ./
```

To deploy the customized resources you can use the following command (note the `-k`):

```
kubectl apply -k ./
```

## Acknowledgements

This deployment was strongly inspired by the work in this aparently abandoned repo:

- [Radicale CalDAV/CardDAV (Kubernetes Edition)](https://github.com/h3ndrk/radicale-k8s)

This deployment depends on the Radicale container images maintained by Thomas Queste:

- [Docker image for Radicale calendar and contact server + security + addons](https://github.com/tomsquest/docker-radicale)
