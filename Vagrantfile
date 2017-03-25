    #Ansible Master Server

    #file_to_disk = '/Users/vkamlesh/ansible'
    Vagrant.configure(2) do |config|
    #config.ssh.insert_key = 'false'
    config.vm.synced_folder "/Users/vkamlesh/ansible/yml", "/home/ansible/script"
 
        config.vm.define "master" do |master|
            master.vm.box = "centos/7"
            #master.vm.box_check_update = "true"
            master.vm.hostname = "ansible-main"
            master.vm.network "private_network", ip: "192.168.56.121"
            #master.ssh.username = "ansible"
            #master.ssh.password = "super@321"
           
        config.vm.provider "virtualbox" do |v|
            v.memory = "2048"
            #v.customize ['createmedium', 'disk', '--filename', file_to_disk, '--size', '20480']
            #v.customize ['storagectl', '--name', 'SATA Controller', '--add', 'sata', '--controller', 'IntelAhci', '--portcount', '1', '--bootable' 'on' ]
            #v.customize ['storageattach', '--storagectl',  'SATA Controller', '--device', '0', '--port', ' 1', '--type', 'hdd', '--medium', file_to_disk  ]
            #Change the network adapter type and promiscuous mode
            #v.customize ['modifyvm', :id, '--nictype1', 'Am79C973']
            #v.customize ['modifyvm', :id, '--nicpromisc1', 'allow-all']
            #v.customize ['modifyvm', :id, '--nictype2', 'Am79C973']
            #v.customize ['modifyvm', :id, '--nicpromisc2', 'allow-all']
        end

        config.vm.provision "shell", inline: <<-SHELL
        yum install epel-release -y
        yum update -y
        sudo yum install ansible -y
        #Install bridge-utils
        #yum install -y bridge-utils
        SHELL

   end


        #Creating Webserver for testing ansible automation.
        config.vm.define "webserver" do |webserver|
            webserver.vm.box = "ubuntu/xenial64"
            webserver.vm.hostname = "webserver"
            webserver.vm.network "private_network", ip: "192.168.56.122"
            #client.ssh.username = "ansible"
            #client.ssh.password = "test@321"
            
        config.vm.provider :virtualbox do |v|
           v.memory = 1024
        end

        config.vm.provision "shell", inline:  <<-SHELL
        apt-get update
        sudo apt -y update && sudo apt install -y python-minimal
        SHELL

  end


       #Creating APP Server for testing ansible automation.
       config.vm.define "appserver" do |appserver|
          appserver.vm.box = "ubuntu/xenial64"
          appserver.vm.hostname = "appserver"
          appserver.vm.network "private_network", ip: "192.168.56.123"
    
     config.vm.provider :virtualbox do |v|
        v.memory = 1024
     end

      config.vm.provision "shell", inline:  <<-SHELL
      apt-get update
      sudo apt -y update && sudo apt install -y python-minimal
      SHELL
     
  end
   
       #Creating DB Server for testing ansible automation.  
        config.vm.define "dbserver" do |dbserver|
           dbserver.vm.box = "centos/7"
           dbserver.vm.hostname = "dbserver"
           dbserver.vm.network "private_network", ip: "192.168.56.124"
    
       config.vm.provider :virtualbox do |v|
           v.memory = 1024
       end

       config.vm.provision "shell", inline:  <<-SHELL
       yum update -y
       SHELL
     
  end

end
