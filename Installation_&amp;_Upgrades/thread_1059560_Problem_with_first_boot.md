---
title: "Problem with first boot"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Hagablog on 2009-02-03
Okay, what I'm trying to do is boot Ubuntu off a USB flash drive (full install not USB startup disk) on a MacBook 2,1.  Everything goes well on the install, I select my pen drive to install to, install GRUB to it and I'm away.  

Then, with the aid of a U[SB boot cd]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/") I boot up.  I get the standard backwards/forwards waiting bar and just when it should be starting to load I get kicked into the command line with the following message.

[FONT="Courier New"]Starting up ...
1     1.8471001 i8042.c: No controller found.
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter "Help" for a list of built-in commands.

(initramfs)[/FONT]

I have waited for an hour with no change and this keeps coming back.  I've even reinstalled Ubuntu to make sure something didn't go wrong.

Thanks in advance

---

### Post by Hagablog on 2009-02-04
Just so you know, when I installed it I partitioned my Pen Drive.  Looking at the partition table in Apple's Disk Utility the non-Ubuntu partition comes first, this is what the installer did as the drive wasn't partitioned before.  The non-Ubuntu partition is now completely empty save for a couple of hidden files.

---

### Post by Hagablog on 2009-02-07
CORRECTION: 
[FONT="Courier New"]Starting up ...
[ 1.847100] i8042.c: No controller found.
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter "Help" for a list of built-in commands.

(initramfs)[/FONT]

---

