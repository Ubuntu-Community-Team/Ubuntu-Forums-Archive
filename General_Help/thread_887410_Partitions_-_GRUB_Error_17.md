---
title: "Partitions - GRUB Error 17"
date: 2008-08-12
forum: General Help
---

### Post by IfanEllis on 2008-08-12
Hello,

Although a newbie I'm trying to sort a problem on a friends Fujitsu Amilo Pi 2515 laptop with a SATA hard drive, originally loaded with Windows Vista. Unfortunately Windows VISTA wouldn't load,however,the recovery disk provided was for Windows XP. 

I then successfully installed Kubuntu with a view of subsequently installing XP from the Recovery CD. I then tried to install Windows XP, formatted the hard drive and suspect I did something to the partition/(s).

On starting the computer I now get the following message: 

[COLOR="Red"]GRUB Loading stage1.5
GRUB Loading please wait
Error 17[/COLOR]

I've tried to install Windows XP (whilst using the F6 facility to load the Intel Matrix Storage Manager SATA RAID driver – ICH8M-E chips set). Although the SATA driver was loaded the message then appeared:
[COLOR="Red"]“Set up did nor find any hard drives installed ion your computer. Make sure any hard drives are powered on and properly connected...”.[/COLOR] 

I then tried to install Kubuntu but could not proceed past stage 3/6 of install; I suspect because there are problems with the partitions.

I then used the Kubuntu Live Cd to go into Konsole and get the following under using 'fdisk -l':

[COLOR="Red"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee9d8452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451    6  FAT16

Disk /dev/sdb: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x6f727265

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   561651809  1128984683   850999312   6c  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 82, 37) logical=(561651808, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(357, 97, 35) logical=(1128984682, 0, 2)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   666205645   847574255   272052916   6e  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(97, 115, 32) logical=(666205644, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(107, 121, 32) logical=(847574254, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   179662788   359321550   269488144   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(356, 101, 33) logical=(179662787, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(0, 13, 10) logical=(359321549, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?   464871435   464878547       10668+  53  OnTrack DM6 Aux3
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(333, 89, 19) logical=(464871434, 0, 3)
Partition 4 has different physical/logical endings:
     phys=(339, 68, 15) logical=(464878546, 0, 3)
Partition 4 does not end on cylinder boundary.[/COLOR]


I would greatly appreciate any help.

Many thanks

---

### Post by Crafty Kisses on 2008-08-12
This link may help you > [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

