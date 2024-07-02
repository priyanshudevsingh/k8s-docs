# Kubernetes on Cloud

To run a Kubernetes (k8s) cluster on a cloud provider like AWS, GCP, DigitalOcean, or Vultr, follow these steps. The instructions will cover creating a cluster, configuring your local environment, and deploying an application.

### 1. **AWS (Amazon Web Services)**

#### Create a Kubernetes Cluster with EKS (Elastic Kubernetes Service)
1. **Sign in to AWS Management Console**:
- Navigate to the EKS service.
- Click "Create cluster".
- Configure your cluster name, role, networking, and logging.
- Create the cluster and wait for it to become active.

2. **Install AWS CLI and eksctl**:
- AWS CLI: [Installation guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- eksctl: [Installation guide](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)

3. **Create EKS Cluster using eksctl**:
```sh
eksctl create cluster --name my-cluster --region us-west-2 --nodegroup-name my-nodes --node-type t2.micro --nodes 3
```

4. **Configure kubectl**:
```sh
aws eks --region us-west-2 update-kubeconfig --name my-cluster
```

### 2. **GCP (Google Cloud Platform)**

#### Create a Kubernetes Cluster with GKE (Google Kubernetes Engine)
1. **Sign in to Google Cloud Console**:
- Navigate to the GKE service.
- Click "Create cluster".
- Configure your cluster name, location, and node settings.
- Create the cluster.

2. **Install Google Cloud SDK**:
- [Installation guide](https://cloud.google.com/sdk/docs/install)

3. **Initialize the SDK and configure kubectl**:
```sh
gcloud init
gcloud container clusters create demo-cluster --machine-type=e2-micro --zone=asia-south2-a --num-nodes=3
gcloud container clusters list
```

### 3. **DigitalOcean**

#### Create a Kubernetes Cluster with DigitalOcean Kubernetes (DOKS)
1. **Sign in to DigitalOcean Console**:
- Navigate to the Kubernetes service.
- Click "Create a Kubernetes Cluster".
- Configure your cluster name, region, and node pool.
- Create the cluster.

2. **Install doctl**:
- [Installation guide](https://docs.digitalocean.com/reference/doctl/how-to/install/)

3. **Download kubeconfig**:
```sh
doctl kubernetes cluster kubeconfig save my-cluster
```

### 4. **Vultr**

#### Create a Kubernetes Cluster with Vultr Kubernetes Engine (VKE)
1. **Sign in to Vultr Console**:
- Navigate to the Kubernetes service.
- Click "Deploy Cluster".
- Configure your cluster name, region, and node pool.
- Deploy the cluster.

2. **Download kubeconfig**:
- Navigate to your cluster details.
- Download the kubeconfig file.

### Replace `~/.kube/config` with the Credentials File
Download the credentials file from the respective cloud provider and replace your local kubeconfig:
```sh
mv path-to-downloaded-kubeconfig ~/.kube/config
```
