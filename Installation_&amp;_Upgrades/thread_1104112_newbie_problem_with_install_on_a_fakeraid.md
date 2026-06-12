---
title: "newbie problem with install on a fakeraid"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by jas51384 on 2009-03-23
hello,
i'm trying to install Ubuntu 8.10 amd64 on a fakeraid array with Windows Vista x64 installed first. i found a tutorial in the archives followed it to the install point, it installs all the way then i get  pop up that says Ubiquity has stopped working, so i just keep going but i get to point where i type in 
cp /usr/lib/grub/x86_64-pc/* /boot/grub
but it tells me that directory /boot/grub doesn't exsist. so thts what i need help on what do i do? thanks in advance!

---

### Post by Coreigh on 2009-03-23
I am not sure when you say 'fakeraid' if you mean a specific brand of RAID or just a software RAID array. I do know that software RAID is handled differently by Windows and Linux. And they are usually incompatible. You may be able to shed some light by running > sudo fdisk -l from a terminal window while booted from the LiveCD. This will list the physical partitions on the disks. However from what I have read in the past dual-booting on a RAID array will only work if the it is real hardware RAID because the disk volume creation is done independently of any OS or software and so appears as a physical disk to any OS.

---

### Post by jas51384 on 2009-03-23
the raid controller is onboard the motherboard, Asus M2N-SLI, set up in Raid0.this is the link to the archived post that im talking about,
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
i installed dmraid and set up the partions and sarted the install. when the install finishes i get a pop up that says Ubiquity stopped working. i follow the rest of the tutorial till it asks to do this 
cp /usr/lib/grub/x86_64-pc/* /boot/grub
but it tells me that directory /boot/grub doesn't exsist. so i don't know why is says ubiquity stops working is doesn't say it can't install grub unless thats what this means

---

### Post by jas51384 on 2009-03-24
I used the alt. install cd and had no trouble. works like a charm
thanks for all the help

---

