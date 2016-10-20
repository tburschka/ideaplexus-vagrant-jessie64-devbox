# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

BOX        = "debian/jessie64"
BOX_MEMORY = 1024

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # define box
  config.vm.box = BOX
  config.vm.box_check_update = true

  # define ssh options
  config.ssh.insert_key = false

  # modify box configuration
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", BOX_MEMORY]
  end

  # set auto_update to false, if you do NOT want to check the correct
  # additions version when booting this machine
  config.vbguest.auto_update = true

  # do NOT download the iso file from a webserver
  config.vbguest.no_remote = false

  # prevent Vagrant from mounting the default /vagrant synced folder
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # mount provisioning scripts and files
  config.vm.synced_folder "./provisioning", "/provisioning", owner: "vagrant", group: "vagrant"

  # define system
  config.vm.provision :shell, path: "./provisioning/scripts/base.sh"
  config.vm.provision :shell, path: "./provisioning/scripts/debian-jessie.sh"

  # required scripts
  config.vm.provision :shell, path: "./provisioning/scripts/ssh.sh", name: "install vcs packages"
  config.vm.provision :shell, path: "./provisioning/scripts/update-upgrade.sh", name: "upgrade packages"
  config.vm.provision :shell, path: "./provisioning/scripts/common-configs.sh", name: "set common configurations"
  config.vm.provision :shell, path: "./provisioning/scripts/common-packages.sh", name: "install common packages"
  config.vm.provision :shell, path: "./provisioning/scripts/locale.sh", name: "set locale"

  # run installation
  config.vm.provision :shell, path: "./provisioning/scripts/vcs.sh", name: "install several vcs"
  config.vm.provision :shell, path: "./provisioning/scripts/git-prompt.sh", name: "install git prompt"
  config.vm.provision :shell, path: "./provisioning/scripts/ntp.sh", name: "install NTP"
  config.vm.provision :shell, path: "./provisioning/scripts/ruby.sh", name: "install Ruby"
  config.vm.provision :shell, path: "./provisioning/scripts/bundler.sh", name: "install Bundler"
  config.vm.provision :shell, path: "./provisioning/scripts/redis.sh", name: "install Redis"
  config.vm.provision :shell, path: "./provisioning/scripts/oracle-java8-installer.sh", name: "install Oracle JDK 8"
  config.vm.provision :shell, path: "./provisioning/scripts/ant.sh", name: "install Ant"

  config.vm.provision :shell, path: "./provisioning/scripts/nodejs-6.sh", name: "install NodeJS 6"
  config.vm.provision :shell, path: "./provisioning/scripts/yarn.sh", name: "install Yarn"
  config.vm.provision :shell, path: "./provisioning/scripts/nginx.sh", name: "install NGINX"
  config.vm.provision :shell, path: "./provisioning/scripts/php-7.sh", name: "install PHP 7"
  config.vm.provision :shell, path: "./provisioning/scripts/mariadb.sh", name: "install MariaDB"
  config.vm.provision :shell, path: "./provisioning/scripts/memcached.sh", name: "install Memcached"
  config.vm.provision :shell, path: "./provisioning/scripts/postgresql.sh", name: "install PostgreSQL"
  config.vm.provision :shell, path: "./provisioning/scripts/phpmemcachedadmin.sh", name: "install PHP Memcached Admin"
  config.vm.provision :shell, path: "./provisioning/scripts/phpredmin.sh", name: "install PHPRedmin"
  config.vm.provision :shell, path: "./provisioning/scripts/elasticsearch.sh", name: "install Elasticsearch"
  config.vm.provision :shell, path: "./provisioning/scripts/elasticsearch-hq.sh", name: "install ElasticHQ"
  config.vm.provision :shell, path: "./provisioning/scripts/mailcatcher.sh", name: "install Mailcatcher"
  config.vm.provision :shell, path: "./provisioning/scripts/jenkins.sh", name: "install Jenkins"

  # clean up
  config.vm.provision :shell, path: "./provisioning/scripts/cleanup.sh", name: "cleanup box"

end
