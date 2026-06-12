---
title: "Ejecting USB devices"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by notebooktessler on 2007-07-24
Hi, 

In Ubuntu 6.10 I used to eject USB devices via the "eject" command in the terminal, but in 7.04 this does not work any more. It says: 
> umount: /media/disk is not in the fstab (and you are not root)
eject: unmount of `/media/disk' failed


Ejecting works, if I right-click on the context-menu of the stick on the desktop, but I'd really like to do it on the command line. 

Is there a way to get Ubuntu do what I want again?

---

### Post by notebooktessler on 2007-07-24
Seems to be a bug...

[https://bugs.launchpad.net/ubuntu/+source/eject/+bug/111541](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/111541)

---

### Post by wiebers10 on 2007-07-24
It works fine on my laptop with 7.04.  Make sure you use sudo umount media/disk not just umount media/disk.  For some reason when doing it from the command line you have to use sudo.

---

### Post by notebooktessler on 2007-07-24
Sure that works. But in 6.10 it used to work (and really SHOULD still work) without "sudo": why should a user need su-privileges to unmount his usb stick??

---

