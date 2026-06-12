---
title: "initramfs on first boot from USB"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Hagablog on 2009-02-07
I have installed Ubuntu to a USB flash drive (full install not USB startup disk) and when I boot it up for the first time it does the standard backwards/forwards waiting bar and just when it should be starting to load I get kicked into the command line with the following message.  

[FONT="Courier New"]Starting up ...
[ 1.847100] i8042.c: No controller found.
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter "Help" for a list of built-in commands.

(initramfs)[/FONT]

I have, according to Disk Utility one my Mac, got three partitions.  1) Fat which I want to keep to use as a pendrive; 2) my Ubuntu partition and 3) a Linux Swap partition which I believe is GRUB but I'm a total Linux noob so I'm probably wrong.  I tried to follow the instructions on [http://www.linuxquestions.org/questions/linux-newbie-8/busybox-shows-up-with-initramfs-prompt-on-usb-installed-ubuntu-8.10-and-8.04-679684/]("http://www.linuxquestions.org/questions/linux-newbie-8/busybox-shows-up-with-initramfs-prompt-on-usb-installed-ubuntu-8.10-and-8.04-679684/") using the LiveCD but I couldn't find any mention of [FONT="Courier New"]/dev/sd[/FONT]X in boot/grub/menu.lst.

---

