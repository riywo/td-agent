Vagrant.configure("2") do |vagrant|
  define_list = [
    {
      :define  => :redhat,
      :box     => "Berkshelf-CentOS-6.3-x86_64-minimal",
      :box_url => "http://dl.dropbox.com/u/31081437/Berkshelf-CentOS-6.3-x86_64-minimal.box",
      :pkgm    => :yum,
    },
    {
      :define  => :debian,
      :box     => "precise64",
      :box_url => "http://files.vagrantup.com/precise64.box",
      :pkgm    => :apt,
    },
  ]

  vagrant.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", 256]
    v.customize ["modifyvm", :id, "--cpus", 4]
  end

  define_list.each_with_index do |define, i|
    vagrant.vm.define define[:define] do |config|
      config.vm.box     = define[:box]
      config.vm.box_url = define[:box_url]

      config.vm.hostname = define[:define].to_s
      config.vm.network :private_network, ip: "192.168.50.#{i + 10}"
    end
  end
end
