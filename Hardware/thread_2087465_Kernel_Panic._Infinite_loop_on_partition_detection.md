---
title: "Kernel Panic. Infinite loop on partition detection."
date: 2012-11-23
forum: Hardware
---

### Post by Mateus Rachid on 2012-11-23
First of all, hi everybody! As I'm new here, sorry if I posted in wrong place, or any other mistake. And sorry for my poor English too.
 
My problem is: I can't boot anything with my SATA hard drive plugged in.
It has a few partitions, and during boot, Ubuntu seems to be detecting the same partitions over and over again within a loop, setting them as sda1, sda2, ... sda168, sda169... and this way it goes, until it runs out of memory and halts on a kernel panic.
 
How could I access this drive to backup my personal files? Since isn't possible to boot almost anything with it plugged, and (AFAIK) I can't hot plug the SATA connection.
Is there some bootable tool where I can fix or just clear the partition table to boot a OS and later recover the partitions manually, or something of this kind?
 
Some info:
* No Windows installed on other drives (or Windows Installer DVD) boot. They hang in the load screen.
* No Linux liveCD boot. Same Kernel Panic error.
* I can navigate just fine through the file systems in the HD using the GRUB2 interactive shell. It detects the partitions nicely.
 
Any help will be really appreciated.
Thanks in advance :)

---

