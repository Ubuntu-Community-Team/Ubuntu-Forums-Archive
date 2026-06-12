---
title: "Mounting old Hard Drive with Raid Partition"
date: 2014-01-27
forum: Hardware
---

### Post by Chris_Nicol on 2014-01-27
I am trying to mount an old hard drive with some sort of RAID Partition.  There is only one drive so I am not sure how the RAID works.  I have had no luck mounting the drive.  Any help would be appreciated.  I have tried many things.  If I simply try to mount it without specifiying a partition type it says it must be specified.  The contents of a fdisk -l command are below.  Any help that can be given would be appreciated.

   Disk /dev/sda: 21.5 GB, 21474836480 bytes  
 255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x0002cda8  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *        2048    39845887    19921920   83  Linux  
 /dev/sda2        39847934    41940991     1046529    5  Extended  
 /dev/sda5        39847936    41940991     1046528   82  Linux swap / Solaris  
 

 Disk /dev/sdc: 500.1 GB, 500107862016 bytes  
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x0dd0c4c6  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdc1   *       16065     2120579     1052257+   4  FAT16 <32M  
 /dev/sdc2         2120580     6329609     2104515   82  Linux swap / Solaris  
 /dev/sdc3         6329610     6474194       72292+  83  Linux  
 /dev/sdc4         6474195   976773167   485149486+  85  Linux extended  
 /dev/sdc5         6474196   976768064   485146934+  fd  Linux raid autodetect  

Thanks Chris

---

### Post by oldfred on 2014-01-27
RAID has meta-data on the drive. You probably need to remove the RAID meta-data to get it to work as a single drive.

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

