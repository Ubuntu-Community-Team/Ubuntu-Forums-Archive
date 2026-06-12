---
title: "PXE Boot off a Windows machine"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by benjamini on 2009-06-11
Trying to install on a laptop with no CD drive via a PXE network boot off a Windows machine using Tftpd32.

i followed the instructions at:

 [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

(modifed the download link for netboot for jaunty, although I got the same error with interpid


I'm able to get the "install" screen up on client computer, then it says "loading..boot failed" and I get the following error on the server computer:
"File : error 131 in system call ReadFile An attempt was made to move the file pointer before the beginning of the file. [07/06 19:13:15.484]" 

Any insight?  I thought it might be a problem caused during the extraction but even tried it by downloading th file direct from:



[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)





 Any insight?

---

### Post by benjamini on 2009-06-11
[f]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux")orgot to mention, the file that is getting the error is:

netboot/ubuntu-installer/i386/linux

---

### Post by martinx73 on 2009-09-20
hi

i have the same problem

please help

thanks in advance

---

### Post by martinx73 on 2009-09-24
solved !
not use jaunty, use ubuntu 8.04
0 errors
please verify bug in netboot image of jaunty 
regards

---

