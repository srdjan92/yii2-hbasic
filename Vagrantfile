# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.box_version = "20190807.0.0"
    config.vm.network "private_network", ip: "192.168.39.99"
    config.vm.hostname = "basic-heroku.local"
    config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=666"]

    config.vm.provider :virtualbox do |v|
	  v.customize ["modifyvm", :id, "--memory", 4096]
	  v.name = 'basic-heroku'
	end

	config.vm.provision "shell", path: "vagrant/provision.sh", privileged: true
	config.vm.provision "shell", path: "vagrant/configure-nginx.sh", run: "always", privileged: true

    config.vm.provision "shell", run: "always", privileged: false, inline: <<-EOF
    echo "Your vagrant machine is loaded at hosts config: 192.168.39.99 basic-heroku.local"
	echo "Please add this configuration in your hosts file located on /etc/hosts on Linux od Windows/System32/drivers/etc/hosts on Windows."
EOF

end