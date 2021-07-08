Vagrant.configure("2") do |config|
  vm_box = "centos/7"
  config.vm.define "app1" do |app1|
    app1.vm.box = vm_box
    app1.vm.hostname = 'ubuntu-app1'
    app1.vm.network "private_network", ip: "192.168.10.221"
    app1.vm.provision "file", source: "/home/sergey/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
    app1.vm.provision "shell", inline: "sudo cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"
    app1.vm.provision "shell",
      inline: <<-SCRIPT_DOC
        yum install -y python
      SCRIPT_DOC
  end

  config.vm.define "db1" do |db1|
    db1.vm.box = vm_box
    db1.vm.hostname = 'ubuntu-db1'
    db1.vm.network "private_network", ip: "192.168.10.222"
    db1.vm.provision "file", source: "/home/sergey/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
    db1.vm.provision "shell", inline: "sudo cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"
    db1.vm.provision "shell",
      inline: <<-SCRIPT_DOC
        yum install -y python
      SCRIPT_DOC
  end
end
