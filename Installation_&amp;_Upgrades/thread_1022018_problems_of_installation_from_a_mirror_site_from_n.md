---
title: "problems of installation from a mirror site from network"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by weyllor on 2008-12-26
I tried to install ubuntu-server in the following steps:
1. down load the files: "linux" and "initrd.gz" from the ubuntu-server.8.04.1.iso/netboot, and copy them to a available path, such as "c:/".
2. install the grub for multi boot.
3. edit the menu.lst and add a item:
[CENTER]title Install Ubuntu
root (hd0,0) 
kernel (hd0,0)/linuz
initrd (hd0,0)/initrd.gz[/CENTER]
4. reboot and use the install item.
5. when the installer ask for mirror site, i specify the [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/).
and finally, the install finished without any errors.
 my question is is found what i installed is the desktop version not server version:
[CENTER]ii linux-generic 2.6.24.22.24 Complete Generic Linux kernel
ii linux-image-2.6.24-22-[COLOR="red"]generic[/COLOR] 2.6.24-22.45 Linux kernel image for version 2.6.24 on x86
ii linux-image-[COLOR="red"]generic[/COLOR] 2.6.24.22.24 Generic Linux kernel image[/CENTER]

compared with the cd installed info:
ii linux-image-2.6.24-19-server 2.6.24-19.41 Linux kernel image for version 2.6.24 on x86
ii linux-image-server 2.6.24.19.21 Linux kernel image on Server Equipment.
ii linux-server 2.6.24.19.21 Complete Linux kernel on Server Equipment.

would some one help me how to specify the server version to the installer when i use the install method above?

thanks a lot.

---

