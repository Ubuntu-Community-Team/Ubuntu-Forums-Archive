---
title: "Installing boot loader to root partition"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by rm42 on 2009-05-04
I have been using Linux for a while now and have several distros installed on my machine.  I decided to give Ubunto 9.0.4 a try and decided to install it on an existing partition (sda10).  I told the installer to place the boot loader on that same partition.  However, when I mount the partition containing the new installation the \boot directory does not have a \grub subdirectory.    
I am used to doing it that way so that I don't risk messing up my existing menu.lst file.  After installing a new distro, I simply mount the partition of the new install, open the menu.lst file and copy the menu entry into my existing menu.lst.  I have tried it twice with the same result.  This looks like a bug to me.  Can anyone confirm this please.

---

