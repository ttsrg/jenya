Vagrant.configure("2") do |config|
  # Base Vagrant Box,
  # CentOS 7.5 Minimal,
  # 20 GB HDD, nothing extra
 # config.vm.box = "sbeliakou/centos"
 # config.vm.box_version = "7.6"

  # VM IP Address in the Private Network

  # Host's hostname master
    config.vm.define "jenya" do |config|
     config.vm.box = "sbeliakou/centos"
     config.vm.box_version = "7.6"
     config.vm.network :private_network, ip: "192.168.56.200"
     config.vm.hostname = "jenya"
     config.ssh.insert_key = false
     config.vm.provider "virtualbox" do |vb|
       # Virtualbox VM name
       vb.name = "jenya"
       # no matter how much CPU is used in the VM, 
       # no more than 50% would be used on your own host machine
       vb.customize ["modifyvm", :id, "--cpuexecutioncap", "30"]
       # RAM provided to VM
       vb.memory = "4096"
     end
     config.vm.synced_folder "host/", "/opt/jenkins", owner: "jenkins",
       group: "jenkins", mount_options: ["uid=5000", "gid=5000"]
     
 # config.vm.provision "shell", path: "master.sh", keep_color: true
  config.vm.provision "shell", inline: "echo ---=== done MASTER===----"
  end

  # Host's hostname slave2
    config.vm.define "jenyaslv2" do |config|
     config.vm.box = "sbeliakou/centos"
     config.vm.box_version = "7.6"
     config.vm.network :private_network, ip: "192.168.56.202"
     config.vm.hostname = "jenyaslv2"
     config.ssh.insert_key = false
     config.vm.provider "virtualbox" do |vb|
       # Virtualbox VM name
       vb.name = "jenyaslv2"
       # no matter how much CPU is used in the VM,
       # no more than 50% would be used on your own host machine
       vb.customize ["modifyvm", :id, "--cpuexecutioncap", "30"]
       # RAM provided to VM
       vb.memory = "2048"
     end
     config.vm.synced_folder "host2/", "/opt/jenkins", owner: "jenkins",
       group: "jenkins", mount_options: ["uid=5000", "gid=5000"]

#  config.vm.provision "shell", path: "jenyaslv2.sh", keep_color: true
  config.vm.provision "shell", inline: "echo ---=== done SLAVE2===----"
  end

  # Host's hostname slave1
    config.vm.define "jenyaslv1" do |config|
     config.vm.box = "sbeliakou/centos"
     config.vm.box_version = "7.6"
     config.vm.network :private_network, ip: "192.168.56.201"
     config.vm.hostname = "jenyaslv1"
     config.ssh.insert_key = false
     config.vm.provider "virtualbox" do |vb|
       # Virtualbox VM name
       vb.name = "jenyaslv1"
       # no matter how much CPU is used in the VM,
       # no more than 50% would be used on your own host machine
       vb.customize ["modifyvm", :id, "--cpuexecutioncap", "30"]
       # RAM provided to VM
       vb.memory = "2048"
     end
     config.vm.synced_folder "host1/", "/opt/jenkins", owner: "jenkins",
     group: "jenkins", mount_options: ["uid=5000", "gid=5000"]
     config.vm.synced_folder "sonar/", "/opt/sonar", owner: "sonar",
     group: "sonar", mount_options: ["uid=6000", "gid=6000"]

#  config.vm.provision "shell", path: "jenyaslv1.sh", keep_color: true
  config.vm.provision "shell", inline: "echo ---=== done SLAVE1===----"
  end


end
