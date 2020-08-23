Ansible Playbooks for Setting Up a Kubernetes Cluster
=====================================================

Ansible playbooks for setting up a stacked highly availabile Kubernetes cluster with Docker and kubeadm.

How to Use
--------------

Execute playbooks/commands in the following order. If you already have ansible user set up, skip Step 0.

Note that users and directories specified in the playbooks mostly assume default settings of Ubuntu 20.04 on Raspberry Pi 4B.

0. ansible-playbook add-ansible-user.yml --ssh-common-args="-o StrictHostKeyChecking=accept-new"
1. ansible-playbook install-docker.yml
2. ansible-playbook install-kubeadm.yml
3. ansible-playbook setup-master.yml
4. Copy kubeadm join commands in {{ kubeadm-init-out }} to join-nodes.yml
5. ansible-playbook join-nodes.yml
6. ansible-playbook change-cgroup-driver.yml
