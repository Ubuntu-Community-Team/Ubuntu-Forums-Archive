---
title: "Presario CQ50 Installation Freeze *Fix*"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Orbital_sFear on 2009-01-15
My Mom bought a compaq Presario CQ50 from Office Depot.  She has always wanted to try Ubuntu so here was my chance.

I installed Ubuntu Ibex 8.10 using Wubi.  The windows part went fine.  

1.  I reboot and found myself sitting in initramfs.  If the NTF mount is marked as unclean, then Wubi installs can't boot.  I booted into windows, told windows to shutdown (not reboot).  Once the computer off, I powered up and went into Ubuntu.
2.  During the ubuntu boot I got a kernel panic.  The module ath_pci isn't compatible with the wireless card in the computer.  I powered off, physically removed the wireless card, and booted the computer back up.
3.  After Wubi was done installing I black listed the bad modules.
[LIST]
[*]vi /etc/modprobe.d/blacklist
[*]blacklist ath_pci
[*]blacklist ath_hal
[*]blacklist pcspkr
[/LIST]
4.  I powered off the computer.
5.  I installed the wireless card back into the computer
6.  Boot up ubuntu
7.  I clicked System -> Administration -> Hardware Drivers -> Uncheck atheros support
8.  I downloaded the working version of the autherous card driver: 
[LIST]
[*]This is what I use but I can't find it anymore: madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
[*]Any of these will likely work: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
[*]cd /tmp
[*]wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3904-20090115.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3904-20090115.tar.gz)
[*]tar -zxvf madwifi-hal-0.10.5.6-r3904-20090115.tar.gz
[*]cd madwifi-hal-0.10.5.6-r3904-20090115
[*]sudo make
[*]sudo make install
[*]reboot
[/LIST]
9.  Test that the thing works: 
[LIST]
[*]sudo modprobe ath_pci
[*]sudo modprobe ath_hal
[/LIST]
10. If your card livin's up and you successfully connect to a network
[LIST]
[*]vi /etc/modprobe.d/blacklist
[*]#blacklist ath_pci
[*]#blacklist ath_hal
[*]vi /etc/modules
[*]ath_pci
[*]ath_hal
[/LIST]
11.  Reboot, if things boot up, your set until you upgrade your kernel.  I wrote this script to fix that, its ugly but... I'm not forcing you to use it!
12.  The script (advanced)

sudo su
cd /etc/
mkdir madwifi
cd madwifi
(copy) madwifi-hal-0.10.5.6-r3835-20080801.tar.gz into this directory

vi build.sh (insert into build.sh)

#!/bin/bash
cd /etc/madwifi
rm -rf madwifi-hal-0.10.5.6-r3835-20080801/
/bin/tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
/usr/bin/make KERNELRELEASE=$1 KERNELPATH=/lib/modules/$1/build
/usr/bin/make install KERNELRELEASE=$1 KERNELPATH=/lib/modules/$1/build

vi rebuild.rb (insert into rebuild.rb)

#!/usr/bin/ruby
File.open("/boot/grub/menu.lst").readlines.each do |line|
  if line.sub(/#.*/, '') =~ /title/ and @title.nil?
    @title = line.chomp.sub(/.*kernel[^0-9]*/, '')
  end
end
  #Check if our kernel has changes?
if !(`uname -a` =~ /#{@title.to_s}/)
  puts "Kernel Has Changed!"
  `/bin/bash /etc/madwifi/build.sh #{@title}`
end

Change permisions of everything
chmod 755 *

Add the system hook
cd /etc/init.d

Create the hook
vi madwifi (insert into madwifi)

#!/bin/bash
/usr/bin/ruby /etc/madwifi/rebuild.rb

(add you kill scripts for reboot and shutdown)
cd /etc/rc0.d
ln -s /etc/init.d/madwifi K07madwifi
cd /etc/rc6.d
ln -s /etc/init.d/madwifi K07madwifi


Now when the kernel is updated, the script will check that and if it finds you're going to boot into a different kernel version than the one currently loaded, the madwifi driver will automatically be rebuilt, and installed so things work on the next boot up.

I hope this helps someone, I spent hours getting this all computer setup.  Enjoy

~Orby

---

### Post by Bucky Ball on 2009-01-15
Great stuff.

---

