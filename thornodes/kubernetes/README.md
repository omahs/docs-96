---
description: Deploying a THORNode with Kubernetes
---

# Cluster Launcher

## **Deploy a Kubernetes cluster**

In order to deploy all the different services and provide a high availability environment to operate your node, Kubernetes is the preferred scheduling platform. Any production-grade Kubernetes cluster can be used to run and deploy a THORNode. You need your Kubernetes provider to offer external load balancers services type features. Azure, Digital Ocean, GCE, OpenStack are compatible with external load balancers.

{% hint style="info" %}
Terraform is a type of domain-specific language (DSL) used to describe code infrastructure. It is designed to make it easier to create/destroy infrastructure hosted locally or by a provider.
{% endhint %}

This Terraform deployment will deploy a Kubernetes cluster using your VPS provider credentials and EKS service. The cluster will have autoscaling capabilities, which means you don’t have to deal with how many nodes you need to deploy to run your THORNode services.

All the default configurations used in these instructions are for a production environment with enough resources to run your THORNode in good conditions.

{% hint style="warning" %}
**LINUX/MAC is the preferred method of setup.**

Windows should choose either:

1. Deploy a THORNode from a Linux VPS.
2. Use Windows Subsystem for Linux - [https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)
{% endhint %}

## Steps

There are three important steps to getting your node set up, deployed and churned in.

1. [Setting up Cluster](setup-aws.md)
2. [Deploying THORNode Services](../deploying.md)
3. [Joining ("Churning In")](../joining.md)

### Repository Management

Your repository can be organised as follows:

```
./thornode-ops
  |./cluster-launcher
  |./node-launcher
```

All of your set up commands are run in `cluster-launcher` and all of your deploying/joining/managing/leaving commands are run from `node-launcher`

### Running Two or More Nodes

{% hint style="danger" %}
To prevent a catastrophic mistake in handling multiple nodes, set them up on different machines, or use different user profiles on your machine, or in the least, use different repos:
{% endhint %}

```
./thornode-ops
  |./cluster-launcher
  |./node-launcher
./thornode-ops2
  |./cluster-launcher
  |./node-launcher
```

All of your commands can now be run separately.

{% hint style="info" %}
It is heavily advised to not set up nodes on the same provider. Deploy 1 node on Azure, 1 node on Digital Ocean etc.
{% endhint %}
