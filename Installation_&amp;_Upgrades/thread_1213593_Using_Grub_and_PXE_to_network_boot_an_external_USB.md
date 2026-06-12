---
title: "Using Grub and PXE to network boot an external USB Drive"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by ufoy on 2009-07-15
Hi all,

  I would like to know how to use PXE and Grub to network boot a linux installation on an external USB drive.  I have successfully installed Ubuntu using the instructions located here:

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")

  During installation, I chose to install Ubuntu on an external USB drive (/dev/sda2) instead to a internal hard drive.  The laptop in question is quite old, and its hard drive died last week.  Being an old laptop, its BIOS cannot boot using CD-ROM, Floppy, or USB.  

  I have read up on the GRUB manual's [network section]("http://www.gnu.org/software/grub/manual/grub.html#Network"),

[http://www.gnu.org/software/grub/manual/grub.html#Network](http://www.gnu.org/software/grub/manual/grub.html#Network)

 and it seems like its possible for GRUB to pull a remote menu.lst from somewhere else once its loaded.  

  Is it possible to customize a PXE boot setup so that Grub and boot an Ubuntu installation on an external USB drive?  If this is possible, I imagine that it might also be possible to rig this setup to remotely boot any hard drive/partition a computer might have, internal or otherwise (as long as its capable of PXE).

Another Issue:  Grub's manual says it will only work with certain USB devices.  However, since I can't even boot Ubuntu, I don't have the opportunity to check.  If someone can point me in the right direction, I'd very much appreciate it

Thanks in advance!

---

