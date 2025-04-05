## K3s + Argocd + Whoami
### 
### --- Install K3s to Ubuntu 22.04 ---
###
### sudo apt update && sudo apt upgrade -y
### sudo su
### vi /etc/fstab
### swapoff -a
### free -m
### curl -sfL https://get.k3s.io | sh -
### sudo systemctl enable k3s
###
### --- Argocd install ---
###
### sudo kubectl create namespace argocd
### wget https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
### mv install.yaml argocd.yaml
### sudo kubectl apply -n argocd -f argocd.yaml
### sudo kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
### sudo kubectl get svc -n argocd
### sudo kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
### 
### sudo kubectl delete -n argocd -f argocd.yaml
### sudo kubectl delete namespace argocd
###
### --- Kubectl commands ---
###
### kubectl apply -f whoami.yaml
### kubectl get deployment
### kubectl get pods -o wide
### kubectl get svc
### kubectl get ingress
### kubectl get namespace
### kubectl get all -n whoami-ingress
### kubectl get secret
### kubectl describe ingress whoami-ingress
### kubectl get pods -n default
### 
### --- Add git to Argocd ---