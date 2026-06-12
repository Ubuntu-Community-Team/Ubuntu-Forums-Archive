---
title: "Dual boot problems"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by skakillers on 2009-10-08
Hi
I'm trying to set up a dual boot environment on my desktop. I have two internal harddrives, with windows 7 installed on the first drive and the second is a data drive. I shrunk the win7 partition using the windows partition manager, and then installed ubuntu in the empty space. I did the default setup, with one partition for the OS and a swap partition. When I restarted after finishing the install, instead of a grub boot selection screen windows just started up. So I tried to get the windows boot selector to boot ubuntu using easyBCD, to no avail. I'm not really sure where to proceed from here. I've tried reinstalling grub according to guides online, but that didn't help. Would it be much easier if I had ubuntu installed first on the drive?

For reference the HDDs are both 640 gb drives, and the ubuntu partition I made on the first one is around 150 gb.

---

### Post by Mark Phelps on 2009-10-08
If the drive you install Seven to was empty, it's likely it installed two partitions -- a 100MB boot partition, and a regular NTFS partition for everything else.  It's possible that Ubuntu doesn't know how to handle this setup when installing and configuring GRUB.

If you want to know how to configure EasyBCD, go to the NeoSmart Technology forums.  They have tutorials and guides on how to do what you want, as well as a support forum.

---

### Post by skakillers on 2009-10-08
Alright, thanks!

---

