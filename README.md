# EKS-ArgoCD-Handson_Application_manifests

## 概要

Web/APアプリケーションをEKSにデプロイするためのKubernetesマニフェストです。
Argo CDがmainブランチのbaseディレクトリを監視し、アプリ用クラスターのapp名前空間へ反映します。

## 4リポジトリの役割

| リポジトリ | 役割 |
|---|---|
| [Terraform](https://github.com/ys-o/EKS-ArgoCD-Handson_Terraform) | AWSリソースの構築とArgo CDの初期導入 |
| [Argo CDアプリケーション定義](https://github.com/ys-o/EKS-ArgoCD-Handson_ArgoCD_app_of_apps) | Web/AP、ESO、AWS Load Balancer Controllerの子Application定義 |
| [Web/APマニフェスト（本リポジトリ）](https://github.com/ys-o/EKS-ArgoCD-Handson_Application_manifests) | Deployment、Service、Ingress、SecretStore、ExternalSecret |
| [Web/APアプリ資材](https://github.com/ys-o/EKS-ArgoCD-Handson_Application) | PHP、Dockerfile、Nginx設定、GitHub Actionsワークフロー |

## ファイル構成

```text
base/
├── deployment.yaml      # Nginx・PHP-FPMを同じPodに配置（2 Pod）
├── service.yaml         # Web/APのService
├── ingress.yaml         # ALBによる外部公開の設定
├── secretstore.yaml     # Secrets Managerの参照先設定
└── externalsecret.yaml  # RDS認証情報をKubernetes Secretへ反映する設定
```
