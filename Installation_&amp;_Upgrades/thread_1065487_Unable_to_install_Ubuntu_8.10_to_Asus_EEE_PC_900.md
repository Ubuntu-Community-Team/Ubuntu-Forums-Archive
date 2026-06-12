---
title: "Unable to install Ubuntu 8.10 to Asus EEE PC 900"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by ravingsockmonkey on 2009-02-09
I've tried following the below post to get Ubuntu 8.10 installed on my Asus EEE PC 900 netbook, but it will not detect the SSD in when it gets to the Prepare Partitions step (step 4 of 7) of the installation.  In fact nothing shows there at all.  I'm at a loss of how to proceed.  Windows XP is installed on the machine and works fine, but I rather use Ubuntu. :(

I've seen where people seem to be using it on similar machines, so I figure it's something I'm either doing wrong or missing.  Any help would be greatly appreciated!

Thank you in advance :)

> **tommcd said:**
> If you have managed to install Ubuntu by opening a terminal and running **sudo modprobe ide-generic**, and then when you try to boot it just hangs, then you probably need the ide-generic module loaded at bootup. To do this, boot from the Ubuntu live CD, mount your Ubuntu partition, and edit the **/etc/modules** file. Add ide-generic to the file, and save and exit. Then when you boot Ubuntu from the hard drive the module should load on bootup and allow you to boot. See this:
[https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add](https://help.ubuntu.com/community/Loadable_Modules?highlight=(modules)|(add))
So boot from the live CD. Lets say Ubuntu is on /dev/sda1. Open a terminal and run:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/etc/modules
```
Then just add ide-generic to the bottom of the file, and save and exit. Then unmount your Ubuntu partition:
```
sudo umount /dev/sda1
```
Then reboot and (hopefully) the kernel module ide-generic should load on bootup and allow Ubuntu to boot.

---

