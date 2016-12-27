# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
#  config.vm.box = "ubuntu/yakkety64"
  config.vm.box = "fedora/25-cloud-base"

 config.vm.provision :ansible_local do |ansible|
      ansible.playbook       = 'ansible.yml'
      ansible.verbose        = 'vvvv'
      ansible.install        = true
      ansible.limit          = "all" 
      ansible.inventory_path = "inventory"
  end

  config.vm.define "devbox" do |devbox|
    devbox.vm.network "private_network", ip: "192.168.33.101"

    # vagrant plugin install vagrant-vbguest
    devbox.vm.synced_folder ".", "/vagrant", type: "virtualbox"

    devbox.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "1024"
    end
  end
end