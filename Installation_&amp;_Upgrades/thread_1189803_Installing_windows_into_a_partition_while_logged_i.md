---
title: "Installing windows into a partition while logged into ubuntu"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by jellytot on 2009-06-17
Hi, 
  I was wondering, is there a program where you can install windows into a blank partition, but do it without booting from a disk? because everytime I boot from windows disc I always get an error before it starts installing. Some massive error comes up to tell me to CHKDISK and such..

   Any help is appreciated. I made a partition for Ubuntu (ext3) and a partition (ntfs) for windows and also a small partition for linux-swap. I did this in GParted from booting and forcing VESA.

 Thanks.

---

### Post by travisrichardson1980 on 2009-06-17
i've had the best success with dual-booting when i install windows first.

then i boot to my linux livecd, resize the partition to make enough free space, then install linux using the "free disk space" option. or i just set up the partitions manually after changing the windows partition size, and tell linux to "install to existing partitions"

installing linux first and windows after usually doesn't work, unless you're really good at setting up your own boat loader.

set up linux second, and it does the boot loader setup for you. (yay!)

but no, i don't believe there is any way to install windows while being logged in to linux. it's pretty much a one-shot, boot-to-windows-cd-and-install deal.

---

### Post by Malac on 2009-06-17
Don't use parted to format ntfs partitions to install windows onto.
Use windows.
Windows is probably baulking at the ubuntu partition table/mbr.
It will over write the MBR when you install windows so have a backup ready.

---

