---
title: "Burn CD while in Live CD"
date: 2008-08-19
forum: General Help
---

### Post by inteluser on 2008-08-19
I'm trying to install Kubuntu 8.04 from within an Ubuntu 7.10 Live CD.  That is, since the Live environment is all I have working, I downloaded the ISO file in the live environment.  I would prefer to not have to install 7.10 just to download and install 8.04.  I imagined that I might be able to get the process going by mounting the install ISO from within the Live CD, but I get this error:
ubuntu@ubuntu:~$ sudo mount -t iso9660 /home/ubuntu/Desktop/kubuntu-kde4-8.04.1-alternate-i386.iso /kubuntu -o loop=/dev/loop4
ioctl: LOOP_SET_FD: Invalid argument

I get the same error when I don't specify a loop device (i.e., -o loop).

---

