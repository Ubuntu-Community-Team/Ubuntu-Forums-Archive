---
title: "Cannot install wifi driver after kernel upgrade"
date: 2012-08-03
forum: Hardware
---

### Post by daniela9488b on 2012-08-03
I have a dell inspiron 1525 32bits with ubuntu 11.04 gnome 2.32.1, processor architecture i686 and upgraded the kernel from 2.6.38-8 to 2.6.39. Everything appears to be fine except that I no longer have wireless. I tried to install the driver with 'Additional Drivers' and I see that the Broadcom STA wireless driver is no activated. After trying to activate it I get this message: "Sorry, installation of this driver failed.Please have a look at the log file for details: /var/log/jockey.log"
These are the last three lines of the jockey.log file:
2012-08-03 09:43:52,015 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
2012-08-03 09:43:52,016 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-08-03 09:43:52,038 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
I already went through many forums trying to solve this issue and installed and uninstalled many packages (for example bcmwl-kernel-source, broadcom-sta-common and broadcom-sta-source) from terminal or the synaptic package manager but nothing seems to work. 
Also read something about uncommenting something from a black list in /etc/modprobe.d/blacklist.conf but I don't know what I'm supposed to uncomment.
Maybe the kernel version is not adequate. Actually when trying to upgrade the kernel from terminal, version 2.6.39 was not part of the list issued with the 'apt-cache showpkg linux-headers' command. Before that command I issued this other command: 'sudo add-apt-repository ppa:kernel-ppa/ppa'. 
To finally install the kernel I downloaded it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), tried with linux-image-2.6.39-020639rc1-generic_2.6.39-020639rc1.201103300912_i386.deb and installed it with ubuntu software center.

---

### Post by daniela9488b on 2012-08-03
I went back to the former kernel version and applied these commands:

sudo apt-get clean
sudo apt-get autoremove --purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source

I can finally use wireless!

---

