# Acesso ao AWS EKS via kubectl local

### Instalar aws-cli (sudo ou root)
pip3 install awscli

Caso não tenha pip3, instalar:
apt|yum install python3-pip

### Configurar credenciais AWS

aws configure
(inserir credenciais)

### Instalar aws-iam-authenticator (user)

mkdir -p $HOME/.aws/bin

curl -o aws-iam-authenticator https://s3.us-west-2.amazonaws.com/amazon-eks/1.21.2/2021-07-05/bin/linux/arm64/aws-iam-authenticator && chmod +x aws-iam-authenticator && mv aws-iam-authenticator $HOME/.aws/bin && export PATH=$PATH:$HOME/.aws/bin && echo 'export PATH=$PATH:$HOME/.aws/bin' >> ~/.bashrc

### Instalar kubectl (user)

curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl && chmod +x kubectl && mv kubectl .aws/bin

### Configurar kubeconfig
mkdir $HOME/.kube && touch $HOME/.kube/config && export PATH=$PATH:$HOME/.kube && echo 'export PATH=$PATH:$HOME/.kube' >> ~/.bashrc

### Levantamento de informações do cluster EKS

aws eks list-clusters

aws eks describe-cluster --name CLUSTER

aws sts get-caller-identity


aws eks update-kubeconfig --region REGIÃO --name CLUSTER-NOME

aws eks update-kubeconfig --region REGIÃO --name CLUSTER-NOME --role-arn arn:aws:iam::XXXXXXXXXXXX:role/testrole
