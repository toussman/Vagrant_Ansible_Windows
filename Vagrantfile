# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/trusty64"
    master.vm.hostname = "master"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = "256"
    end
    master.vm.network :private_network, ip: "192.168.42.99"
    master.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.install = true
      ansible.limit = "all"
      ansible.inventory_path = "hosts"
    end
  end

  config.vm.define "slave00" do |slave100|
    slave100.vm.box = "ubuntu/trusty64"
    slave100.vm.hostname = "slave00"
    slave100.vm.provider "virtualbox" do |vb|
      vb.memory = "256"
    end
    slave100.vm.network :private_network, ip: "192.168.42.100"
  end

  config.vm.define "slave01" do |slave101|
    slave101.vm.box = "ubuntu/trusty64"
    slave101.vm.hostname = "slave01"
    slave101.vm.provider "virtualbox" do |vb|
      vb.memory = "256"
    end
    slave101.vm.network :private_network, ip: "192.168.42.101"
  end
  
  config.vm.define "slave02" do |slave102|
  slave102.vm.box = "christophershoemaker/win2k8r2sp1.box"
  slave102.vm.box_url = "http://vagrantcloud.com/christophershoemaker/boxes/win2k8r2sp1.box/versions/1/providers/virtualbox.box"
  slave102.vm.hostname = "slave02"
  slave102.vm.guest = :windows
  slave102.vm.communicator = :winrm
  slave102.winrm.username = "vagrant"
  slave102.winrm.password = "vagrant"
  slave102.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    slave102.vm.network :private_network, ip: "192.168.42.102"
  end
end
