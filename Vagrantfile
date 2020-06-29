Vagrant.configure("2") do |config|
  
  config.vm.provider "virtualbox" do |v|
    v.name = "wellthbox"
  end
 
  ## bionic is widely used and stable 
  config.vm.box = "ubuntu/bionic64"


  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  
  ## if you have private networks setup already and this specific ip is used, feel free to alter
  config.vm.network "private_network", ip: "192.168.137.11"

  ## copy your macbooks private key to your vagrantbox
  # config.vm.provision :file, source: "~/.ssh/id_rsa", destination: "/home/ubuntu/.ssh/id_rsa"

  ## typical inline shell script to provision your vm. TODO: use a better provisioner ex. ansible
  ## quick nginx install on vm
  config.vm.provision "shell", inline: <<-SHELL
    apt update
    apt install nginx -y
  SHELL

  ## example of using a provisioning software such as ansible
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "vagrant_provision.yml"
    ansible.install_mode = "default"
  end


end
