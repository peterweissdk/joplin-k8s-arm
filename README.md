# 💾 Joplin Server Helm Chart for ARM Architecture

## 🙏 Attribution

This chart is based on the work from [Rub'x Kube](https://github.com/rubxkube/helm-charts/tree/main/charts/joplin), modified for ARM architecture. This implementation uses [redrathnure's ARM-compatible Joplin container](https://hub.docker.com/r/redrathnure/joplin) as its base image.

## ℹ️ Info

The Traefik IngressRoute is configured for HTTP only, as SSL termination and certificate management are handled externally through pfSense in front of my LAN.

## ✨ Features

- Full Joplin Server deployment optimized for ARM architecture
- Ingress support for easy access
- Persistent storage for your notes and attachments
- Highly configurable through values.yaml
- ARM-compatible images and configurations

## 🚀 Quick Start

To install the Joplin server, run:

```bash
# Install Joplin Helm Chart
helm repo add rubxkube https://rubxkube.github.io/charts/
helm repo update

helm install joplin rubxkube/joplin \
    --namespace joplin-system \
    --create-namespace \
    --values joplin-values.yaml

# Ingressroute for Traefik
kubectl apply -f joplin-ingressroute.yaml
```

## 🔧 Configuration

In the `joplin-values.yaml` file, you can specify the configurable parameters of the Joplin chart and their default values. To override these values, create a `joplin-values.yaml` file and specify your values there.

For detailed configuration options, please refer to the default values in the chart.
https://artifacthub.io/packages/helm/rubxkube/joplin

## 📝 Directory Structure

```
joplin-k8s-arm/
├── joplin-ingressroute.yaml    # Ingressroute configuration for Traefik proxy
├── joplin-values.yaml          # Default configuration values
├── LICENSE                     # License information
└── README.md                   # This documentation
```

## 🔍 Health Check

To check the deployment status:

```bash
kubectl get pods -n joplin-system
kubectl describe pod -n joplin-system <pod-name>
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🆘 Support

If you encounter any issues or need support, please file an issue on the GitHub repository.

## 📄 License

This project is licensed under the GNU GENERAL PUBLIC LICENSE v3.0 - see the [LICENSE](LICENSE) file for details.
