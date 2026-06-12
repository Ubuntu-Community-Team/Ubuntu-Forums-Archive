---
title: "help with syslinux"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by robasc on 2009-03-05
I am working on installing a diskless node but having trouble with copying copying the PXE bootloader code to the tftp server.

Here is the [instructions]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") I am using. I am at section 1.2.



Install syslinux and copy the PXE bootloader code to the tftp server directory. 

$ sudo apt-get install syslinux
$ cp /usr/lib/syslinux/pxelinux.0 /srv/tftp/

Error message:

robert@master-node:~$ sudo cp /usr/lib/syslinux/pxelinux.0 /srv/tftp 
robert@master-node:~$ sudo mkdir /srv/tftp/pxelinux.cfg
mkdir: cannot create directory `/srv/tftp/pxelinux.cfg': Not a directory "what is wrong here!"

---

### Post by jbbjshlws on 2009-04-18
Hello,
I am also having this same issue working off of the same "how to" doc, there is no directory called tftp within srv any ideas anyone?

---

