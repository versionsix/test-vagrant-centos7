Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |v|
    v.memory = 1024
    v.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
  end
  config.vm.define "test-host" do |app|
    app.vm.box = "centos/7"
    app.vm.synced_folder "src/", "/opt/src"
    app.vm.hostname = "test-host"
    app.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/configuration.yml"
    end
  end
end     

