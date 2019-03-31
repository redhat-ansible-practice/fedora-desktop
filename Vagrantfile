# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|

  # Ensure we use our vagrant private key
  config.ssh.insert_key = false
  config.ssh.private_key_path = '~/.vagrant.d/insecure_private_key'

  config.vm.define 'fedora27.local' do |machine|

    machine.vm.box = "fedora/27-cloud-base"
    machine.vm.network :private_network, ip: '192.168.88.27'
    machine.vm.hostname = 'fedora27.local'

    machine.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'tests/test.yml'
      ansible.verbose = "vvv"
      ansible.become = true
      ansible.inventory_path = 'vagrant-inventory'
      ansible.host_key_checking = false
    end

  end


end
