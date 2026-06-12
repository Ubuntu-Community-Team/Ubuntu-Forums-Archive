---
title: "a question :D"
date: 2005-01-23
forum: Installation &amp; Upgrades
---

### Post by akurashy on 2005-01-23
After playing with ubuntu i decided to erase gentoo and installing it on my windows partition, the problem is that i dont know if it going to make my GRUB dual boot problems. and i dont know how to edit GRUB when i install it fully :o

I have installed gentoo before but not with a GRUB in the middle. I mean should i install the GRUB that gentoo brings? so i dont know what to do >_<!

---

### Post by piedamaro on 2005-01-23
Just boot with ubuntu installation cd then follow the installation, it will install grub as boot loader and if you have a windows partition it will be included in the list of available operating systems at startup.

---

### Post by akurashy on 2005-01-23
i dont mean that oO

GRUB is already instaleld in my pc, but what i mean is that 
I have Ubuntu as main OS, and windows as secondary.. im going to delete windows partition to install gentoo, and in a stage of gentoo it says i need to install GRUB (my question is that if i should install GRUB when ubuntu have one installed ?

---

### Post by DJ_Max on 2005-01-23
[QUOTE=akurashy]i dont mean that oO

GRUB is already instaleld in my pc, but what i mean is that 
I have Ubuntu as main OS, and windows as secondary.. im going to delete windows partition to install gentoo, and in a stage of gentoo it says i need to install GRUB (my question is that if i should install GRUB when ubuntu have one installed ?[/QUOTE]
I'm not exactly sure how GRUB works, but if you already have GRUB, no need to install it. Just configure it to boot Gentoo in place of windows.

---

### Post by shmonkey on 2005-01-23
You don't need to reinstall grub when when you install Gentoo. You must make a note of what is installed on what partitions though. The Gentoo handbook will tell you how to edit the grub configuration file manually.

Just nake sure you don't format the partitions with Ubuntu on !

Personally I would install grub from Gentoo (after making a note of the Ubuntu partitions). There are slight differences - the Gentoo handbook will refer to /boot/grub/grub.conf - Ubuntu will refer to /boot/grub/menu.lst.

If you follow the Gentoo handbook - and add Ubuntu to the grub config you should be fine.

---

### Post by akurashy on 2005-01-23
well i can give it a try but then again if i install windows again (suposing im going to*)
then GRUB going to be screwed and a mess >_<

---

