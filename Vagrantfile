ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
IMAGEN = "generic/ubuntu2004"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", type: "rsync"
 
  config.vm.define :server do |s|
    s.vm.box = IMAGEN
    s.vm.hostname = "ansible-menu"
    s.vm.box_check_update = false
    
    s.vm.provision "shell", inline: <<-SHELL 
    sudo apt-get update; sudo apt-get install -y ansible
    SHELL

    s.vm.provider :libvirt do |v|
      v.memory = 1024  
      v.cpus = 2
    end
  end  
end
