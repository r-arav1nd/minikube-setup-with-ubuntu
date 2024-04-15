# <i>minikube</i> setup with Ubuntu Server

<i>minikube</i> is local Kubernetes, focusing on making it easy to lean and develop for Kubernetes.<br>
Setting up minikube on an Ubuntu server involves several steps. Here's a basic outline of the process


## 1. Prerequisites:

 - An Ubuntu server with a supported version (preferably a recent [Ubuntu 22.04 LTS](https://ubuntu.com/download/server) release)
 - SSH access to the server should be enabled.


## 2. Install Docker:

In our minikube setup, we will use the Docker (<i>Containerd</i>) has container runtime
For the latest docker setup with ubuntu, please follow the detailed documentation on [https://docs.docker.com/engine/install/ubuntu](https://docs.docker.com/engine/install/ubuntu/)

> <i>Note:</i><br>
> After installation of docker, please create a <i>docker</i> group and add your users
>
> ```
> :>sudo groupadd docker
> :>sudo usermod -aG docker $USER
> ```
>
> You can also run the following command to activate the changes to groups,
>
> ```
> :>newgrp docker
> ```


## 3. Install <i>kubectl</i>:

The Kubernetes command line tool, <i>kubectl</i> allows you to run command against Kubernetes clusters. For more information on Kubernetes please visit [https://kubernetes.io/docs/tasks/tools/install-kubectl-linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

 - Download the kubectl binary using curl command,

    ```
    :>curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    ```

 - set the execution permission
   ```
   :>chmod +x kubectl
   ```

 - Move the <i>kubectl</i> into <i>/usr/local/bin</i> path
   ```
   :>mv ./kubectl /usr/local/bin/kubectl
   ```


## 4. Install <i>minikube</i>:

Minikube is local Kubernetes, focusing on making it easy to lean and develop for Kubernetes.

Download the minikube from

```
:>curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

and move the setup into <i>/usr/local/bin</i> path

```
:>sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```


## 5. Start <i>minikube</i> using Docker:

Now you can start the minikube with Docker driver

```
:>minikube start --driver=docker
```

The above command will start the minikube on your Ubuntu server
<br>
<br>
> <i>Note:</i><br>
> If you want to stop and delete the existing minikube files, please follow the below command,
> ```
> :>minikube stop
> :>minikube delete --all=true --purge=true
> ```

