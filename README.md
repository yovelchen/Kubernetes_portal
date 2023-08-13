# Deploying Kubernetes Cluster Web Portal

The Kubernetes Cluster Web Portal is a tool that provides information about all the services running within your Kubernetes cluster. This guide will walk you through the deployment process using either ArgoCD or manual installation.

For services to be accessible from outside the cluster, ensure that you set their type as LoadBalancer and assign different ports to each service. Clicking on the HTML link in the web portal will open the service in a new tab with the URL localhost:(defined port).

## Deployment steps
To deploy the portal, you can choose to manually install or use ArgoCD.

### ArgoCD deployment

To deploy on ArgoCD, Open the UI and create a new app with the following fields:  
```
Application Name: cluster-portal  
Project Name: default  
SYNC POLICY: Which ever you like  
AUTO-CREATE NAMESPACE: Check  
Repository URL: //github.com/yovelchen/Kubernetes_portal.git
Path: ./YAML  
Cluster URL: <Your cluster URL>  
Namespace: "cluster-portal"
```

### Manual deployment on Kubernetes
To deploy the portal directly on your cluster, run the following commands:
```
git clone https: //github.com/yovelchen/Kubernetes_portal.git
cd Kubernetes_portal
kubectl create namespace cluster-portal
kubectl apply -f ./YAML
