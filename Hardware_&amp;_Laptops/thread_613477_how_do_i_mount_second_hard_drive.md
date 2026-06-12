---
title: "how do i mount second hard drive"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by lividishere on 2007-11-15
I installed gutsy to a new hard drive but I can't mount the old one that has my documents on it. Help please. I am so newbie it sucks.

---

### Post by delphiguy on 2007-11-15
hmm let me see.

first you have to do sudo fdisk -l to list all the harddrives in your system so that you can get
the device name. it should output something similar to this:  I dont have access to ubuntu
at the moment so this is from memory.
for SATA
/dev/sda
  /dev/sda1

for IDE
/dev/hda
  /dev/hda1

assuming that the drive you want to mount is sda1 you can type this in the console
sudo mount /dev/sda1 /media/mydrive 

be aware that mydrive directory  must first exist.  after that you can see the contents of
the drive, so you can now
ls /media/mydrive

hope this helps.

---

### Post by logos34 on 2007-11-15
If you want it to automount at boot you need to add it to fstab:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

