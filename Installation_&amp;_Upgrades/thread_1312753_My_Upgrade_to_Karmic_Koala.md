---
title: "My Upgrade to Karmic Koala"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by The-REV on 2009-11-03
Hi, folks...

I've recently upgraded my desktop distro from The Jaunty Jackalope (Ubuntu 9.04) to the new release 9.10, The Karmic Koala, perhaps the best Linux ever. Congrats Canonical for this fine free OS and free services (I performed my upgrade online, in few hours, downloading and installing over 1,400 files without only one problem, using a DSL Internet connection). Then I downloaded the live CD.


The only problem is that both upgrade & CD has a bug in network-manager and the user cannot access the Web simply clicking its icon in the Gnome panel at head. But I solved this inconvenience quickly:

First of all I removed the network-manager:
macarlo@macarlo-desktop:~$ sudo apt-get remove network-manager

Then, I performed the steps below:

Configuring resolve.conf with two DNS from my DSL provider:

macarlo@macarlo-desktop:~$ chmod a+r /etc.resolv.conf
macarlo@macarlo-desktop:~$ sudo gedit /etc/resolv.conf

My new resolv.conf is:

nameserver 200.149.55.140
nameserver 200.165.132.147

Editing network interface for automatic Internet connection at boot:

macarlo@macarlo-desktop:~ sudo gedit /etc/network/interfaces

...and y new interfaces is:

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet dhcp


Note that you want not an automatic connection at startup you can do the boot without it and then connect manually doing:

macarlo@macarlo-desktop:~$ sudo pppoeconf

...this will detect your eth, then you have to insert the user name and password used for your ISP and you are done!:p

---

