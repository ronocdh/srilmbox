# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Silly but effective syntax for declaring box hostname
  config.vm.define :nlpbox do |t|
  end

  # Canonical builds nightly Vagrant images for Ubuntu: http://cloud-images.ubuntu.com/vagrant/
#  config.vm.box = "trusty32"
#  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box"
  config.vm.box = "trusty64"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

#  config.vm.network :forwarded_port, guest: 8000, host: 8000
#  config.vm.network :private_network, ip: "192.168.33.33"
#

  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.name = "nlpbox"
  end

#  config.vm.synced_folder "../language-model-server", "/home/vagrant/gits/lmserver"

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
    ansible.inventory_path = "provisioning/ansible_hosts"
    ansible.tags = ["rnnlm"]
    ansible.skip_tags = ["test"]
    ansible.verbose = "extra"
  end

#  config.vm.provision :shell, :path => "provisioning/scripts/deploy_lm_server.sh"
end
