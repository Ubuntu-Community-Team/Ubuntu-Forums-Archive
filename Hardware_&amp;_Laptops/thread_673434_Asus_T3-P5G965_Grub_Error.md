---
title: "Asus T3-P5G965 Grub Error"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by xerman on 2008-01-20
Hello there:

What I am going to state here is something quite strange that has been taking place on my home PC.

Status Quo:
I have 1 PC at home and 1 PC at work:(Both of them):
-ASUS T3-P5G965 Barebones
-2 SATA HD
-IDE DVDRW (not the same one)
-Intel Core2Duo E6300 2GHz
-1 GB ram (home) 2 GB ram (work)
-Bios version 703 (both) (same settings on both)
-Just Ubuntu booting, no dual boot
-Feisty (work), Who knows (home)

At work everything seems to work fine. Feisty (7.04) keeps working with no hard issues. But at home I can not get the computer to work for more than a week.
Partition table is in both like this:

/dev/sda1 - (hd0,0) - /boot  (1024MB on both)
/dev/sda2 - (hd0,1) - /
/dev/sda3 - (hd0,2) - /home
/dev/sda4 - (hd0,3) - /swap

/dev/sdb1 - (hd1,0) - /media/disk1
/dev/sdb2 - (hd1,1) - /media/disk2

grub is on (hd0) on both machines

All partitions are ext3 on both machines.

I think I've been having all kind of Grub errors, from Geometry, Read errors, Error 21, Error whatever .... (All that is being said beneath applies to Gutsy and Feisty. Same issues regardless the version)

The amazing thing is that starting the computer with the LiveCD, wether it is Feisty or Gutsy, sometimes /sda appears an sometimes dissapears. Which means that I cannot get to the info on that drive. Actually, one of the times the drive appeared I copied what was important to the second drive (sdb), and reformat the whole drive. Did a new install with both Feisty and Gusty, (Very time comsuming process duplicated, once with each version), and get the computer to restart with no issues. As soon as that start ends, and do a new restart, the problems start again. 

It is "funny" to notice that seems that depending on the mood of the PC grub sees the drive or does not see the (sda) drive. So it hopefuly gets to gnome some day and some day it does not go beyond Grub Loading Stage 1.5.

Sometimes it gets to gnome and after a while it locks. Restarting GDM produces a console output and system locks up, not being able to log in in any TTY, and not being able to restart/shutdown the computer; but hard shuting down on the computer switch.

Everytime I install i get an sda superblock error on ther root partition and on the home partition before getting to the login screen. This produces a restart, and in this restart is when I finally get to gnome for the first time after install.

If when I start the LiveCD the (sda) device is not seen, I can proceed with the install, and when I get to the partition setup, Voilà!. There it is. (sda) is there with no partition table at all. So the thing is weird, weird.

Noticed too is that 1GB ram DIMM does not show 1024 MB ram, nor in Bios, nor in Ubuntu, shows 1008 MB in Bios and 998 in Ubuntu. So could be due to Ram failure?

I'm starting to think about the following possibilities:
1- Asus machines are something Linux users should be away of.
2- Hard drive (sda) could have some malfunction issue.
3- Grub is not ready for mass production.
4- Buy a Gigabyte mobo with Amd64x2 and move to that hardware

Any kind of help provided would be much appreciated.

Thanks a lot
Regards

Xermán

---

### Post by xerman on 2008-02-03
Hello there,

I solved this issue after a long time. Taking into account that at home most of the time I don't have the computer on.... and all the issues I've been having...

The Grub errors were solved by doing:

> Reformat whole drive and set partition table
/dev/sda1 -> /boot
/dev/sda2 -> /
/dev/sda3 -> /home
/dev/sda4 -> swap

/boot is on the first partition and 1GB size, at the begining of the disk. Seems Mobo from Asus Barebone needs this. I installed Feisty fresh reformating and not keeping any data in any partition. Al partitions Ext3 but SWAP.

This way i do not get the error again. Was the placement of "/boot" what made system go crazy.

Now I get Grub errors when I had to do a Reboot, but that is due to another issues, I presume, as related in thread
[http://ubuntuforums.org/showthread.php?t=683901](http://ubuntuforums.org/showthread.php?t=683901)

about Gnome Vanishes.

Hope this helps
Regards

---

