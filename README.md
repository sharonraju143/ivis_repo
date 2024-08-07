# ivis_repo
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

## Before you deploy the NGINX Ingress Helm chart to the GKE cluster, add the nginx-stable Helm repository in Cloud Shell:

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

## Deploy an NGINX controller Deployment and Service by running the following command:

helm install nginx-ingress ingress-nginx/ingress-nginx

## Verify that the nginx-ingress-controller Deployment and Service are deployed to the GKE cluster:

kubectl get deployment nginx-ingress-ingress-nginx-controller
kubectl get service nginx-ingress-ingress-nginx-controller
