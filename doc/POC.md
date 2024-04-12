# AgroCD POC

1. Запустити minikube :

```console
minikube start
```

2. Створити новий namespace та встановити ArgoCD :

```console
kubectl create namespace argocd && kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

3. Запустити AgroCD :

```console
kubectl port-forward svc/argocd-server -n argocd 8080:443&
```

4. Отримати пароль :

```console
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```

Тепер ви зможете відкрити https://localhost:8080
Увійдіть як admin використовуючи пароль, який отримали на кроці 4.

Demo:
![Image](./POC.gif)
