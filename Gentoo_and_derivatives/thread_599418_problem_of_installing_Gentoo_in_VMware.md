---
title: "problem of installing Gentoo in VMware?"
date: 2007-11-01
forum: Gentoo and derivatives
---

### Post by chunchengch on 2007-11-01
I would like to try Gentoo, so I run the liveCD in the VMware with the NAT network connection setting, while after booting into the Gentoo desktop, I can not connect to the internet, I check the network setting of Firefox, the option "Direct connection to the internet" is checked, it is the same as that of the host operating system (Ubuntu), so is there anything wrong?

Furthermore, I click the installer icon on the desktop to install Gentoo in the VMware, at the final stage, the installation is failed, I suppose that should be the problem of internet connection, am I right?

Concerning the network, I am using Static IP ADSL, I wonder if I adopt the bridge option for the virtual machine to connect directly to the physical network, will it conflict with the network setting of host machine? will it cause any problem when I switch between host machine and virtual machine to surf the internet? 

so I asked the question in VMware forume, the answer is NAT will be the only choice, so I try again to install Gentoo in VMware with NAT network setting, and unfortunately, the installation fails again at the final stage.

Before starting installation, I type command "ifconfig eth0" to check if the network is up, here is the link of snapshot,  I don't know why the network does not work, so can anyone help solving this problem?

[http://picasaweb.google.com/chunchengch/Gentoo/photo#5127836899155483922](http://picasaweb.google.com/chunchengch/Gentoo/photo#5127836899155483922)


Any suggestion is highly appreciated!

---

### Post by Bachstelze on 2007-11-02
The installer in Gentoo's Live CD is known to be awfully buggy, and anyway, why bother with Gentoo if you want automated stuff, right ? ;)

Just do "the real thing" and install Gentoo from scratch ^^

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

---

### Post by chunchengch on 2007-11-08
I installed Gentoo from the scratch with minimal CD, but it failed at auto-configuration of xorg-x11, I tried the semi way, while there was no country option of Taiwan R.O.C., and I was not quite sure about the resolution of terminal, so I stopped the configuration.

Then, I re-installed via liveCD with the option "networkless", finally, Gentoo was successfully installed into the VMware guest, then I solved the problems of "eth0 does not exist" and "can not remove blocking packages" etc., now the Gentoo is proceeding its first update, the update lasts for 24 hours and seems to need more time to finish.:(

Although it is quite difficult and time-consuming to install Gentoo, I have to say it is interesting to learn Gentoo and use it.

---

