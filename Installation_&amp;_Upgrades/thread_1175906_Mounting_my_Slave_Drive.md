---
title: "Mounting my Slave Drive"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by ron3090 on 2009-06-01
I just found a 10 gb drive (which I assume is totally empty) and set it up as the slave drive to my 350 gb xubuntu drive. The drive shows up in the BIOS, and the system info claims it is on scsi0 along with my other drive, but I cannot seem to find the path to it and thus mount it or partition it. Any help?

EDIT: I did an fdisk -l on my 350gb on a hunch, and got this back:

sudo fdisk -l /dev/sda1

Disk /dev/sda1: 319.3 GB, 319305337344 bytes
255 heads, 63 sectors/track, 38819 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

What does this mean? Is my working drive somehow broken?

EDIT: Also, although the drive claims to be SCSI, the cable looks like an IDE cord. I'm not sure what's going on...

---

### Post by Girya on 2009-06-01
see if the other drive shows up with this command: 

> sudo fdisk -l

sudo fdisk -l /dev/sda1 will just show the sda1 partition. when I run fdisk -l on my system I get this:

> kevin@kevin-desktop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9225

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         154     1236973+  83  Linux
/dev/sda2             155       16677   132720997+   5  Extended
/dev/sda3           16678       19202    20282062+  83  Linux
/dev/sda4           19203       19457     2048287+  82  Linux swap / Solaris
/dev/sda5             156         395     1927800   83  Linux
/dev/sda6             396        2945    20482843+  83  Linux
/dev/sda7            2946        8044    40957686   83  Linux
/dev/sda8            8045       16677    69344541   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82718271

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1158     9301603+   b  W95 FAT32
/dev/sdb2            1159        4865    29776477+  83  Linux


If I run sudo fdisk -l /dev/sda1 I get the same complaint as you: 

> kevin@kevin-desktop:~$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 1266 MB, 1266660864 bytes
255 heads, 63 sectors/track, 153 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table


The reason fdisk complains is because there is no partition table in the partition sda1, the partition table for sda is in the MBR on sda. I hope my explanation makes sense. fdisk is meant to work on devices to create partitions.

---

### Post by ron3090 on 2009-06-01
fdisk -l gives this:
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38820   311821618+  83  Linux
/dev/sda2           38821       38913      747022+   5  Extended
/dev/sda5           38821       38913      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 1017 MB, 1017643008 bytes
29 heads, 60 sectors/track, 1142 cylinders
Units = cylinders of 1740 * 512 = 890880 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1143      993667+   6  FAT16

I assume that /dev/sdb is the drive, so I did sudo fdisk /dev/sdb, and got this:
> sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xdaee4784.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1216.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help):

I'm not sure what I'm doing from here. I want to format it to install windows onto, so how?

---

