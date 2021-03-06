# -*- mode: ruby -*-
# vi: set ft=ruby :

## Vagrant :: Centos 6.5 + MongoDB 2.6 with Replica Set of 3 nodes :: Vagrant File ##

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config| 

    # Base box
    config.vm.box = "puppetlabs/centos-6.5-64-puppet"

    # VM config
    # Node 1
    config.vm.define :node1 do |node_conf|
        node_conf.vm.network :private_network, ip: "10.11.12.11"
        node_conf.vm.network :forwarded_port, host: 27017, guest: 27017

        node_conf.vm.hostname = "node1"

        node_conf.vm.provider 'virtualbox' do |v|
            v.customize ['modifyvm', :id, '--groups', '/rstest']
            v.customize ['modifyvm', :id, '--name', 'node1']
            v.customize ['modifyvm', :id, '--cpus', '1']
            v.customize ['modifyvm', :id, '--memory', 512]
            v.customize ['modifyvm', :id, '--ioapic', 'off']
            v.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
            v.customize ['modifyvm', :id, '--nictype1', 'virtio']
            v.customize ['modifyvm', :id, '--nictype2', 'virtio']
        end

        # Update package list
        node_conf.vm.provision :shell, :inline => 'if [[ ! -f /yum-run ]]; then sudo yum check-update; sudo touch /yum-run; fi'

        # Puppet provision
        node_conf.vm.provision :puppet do |puppet|
            puppet.manifests_path   = 'manifests'
            puppet.manifest_file    = 'node.pp'
            puppet.module_path      = 'modules'
            puppet.options          = ['--verbose']
        end
    end

    # Node 2
    config.vm.define :node2 do |node_conf|
        node_conf.vm.network :private_network, ip: "10.11.12.12"
        node_conf.vm.network :forwarded_port, host: 27018, guest: 27017

        node_conf.vm.hostname = "node2"

        node_conf.vm.provider 'virtualbox' do |v|
            v.customize ['modifyvm', :id, '--groups', '/rstest']
            v.customize ['modifyvm', :id, '--name', 'node2']
            v.customize ['modifyvm', :id, '--cpus', '1']
            v.customize ['modifyvm', :id, '--memory', 512]
            v.customize ['modifyvm', :id, '--ioapic', 'off']
            v.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
            v.customize ['modifyvm', :id, '--nictype1', 'virtio']
            v.customize ['modifyvm', :id, '--nictype2', 'virtio']
        end

        # Update package list
        node_conf.vm.provision :shell, :inline => 'if [[ ! -f /yum-run ]]; then sudo yum check-update; sudo touch /yum-run; fi'

        # Puppet provision
        node_conf.vm.provision :puppet do |puppet|
            puppet.manifests_path   = 'manifests'
            puppet.manifest_file    = 'node.pp'
            puppet.module_path      = 'modules'
            puppet.options          = ['--verbose']
        end
    end

    # Node 3
    config.vm.define :node3 do |node_conf|
        node_conf.vm.network :private_network, ip: "10.11.12.13"
        node_conf.vm.network :forwarded_port, host: 27019, guest: 27017

        node_conf.vm.hostname = "node3"

        node_conf.vm.provider 'virtualbox' do |v|
            v.customize ['modifyvm', :id, '--groups', '/rstest']
            v.customize ['modifyvm', :id, '--name', 'node3']
            v.customize ['modifyvm', :id, '--cpus', '1']
            v.customize ['modifyvm', :id, '--memory', 512]
            v.customize ['modifyvm', :id, '--ioapic', 'off']
            v.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
            v.customize ['modifyvm', :id, '--nictype1', 'virtio']
            v.customize ['modifyvm', :id, '--nictype2', 'virtio']
        end

        # Update package list
        node_conf.vm.provision :shell, :inline => 'if [[ ! -f /yum-run ]]; then sudo yum check-update; sudo touch /yum-run; fi'

        # Puppet provision
        node_conf.vm.provision :puppet do |puppet|
            puppet.manifests_path   = 'manifests'
            puppet.manifest_file    = 'node.pp'
            puppet.module_path      = 'modules'
            puppet.options          = ['--verbose']
        end
    end
end
