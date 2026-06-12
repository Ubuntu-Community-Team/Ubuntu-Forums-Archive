---
title: "Possible Backup Partition?"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-08-13
1. Is there a way to install and have a backup partition that is mountable to add and remove files, but is untouched by the system otherwise?

2.When a full disk install is done, does it remove all MS from the MBR?

Thank you to all that help. 

I am backing up files now to prepare for a full HD single boot install. Time to send MS and Fedora packing.

---

### Post by presence1960 on 2009-08-13
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2            5223       19843   117443182+  83  Linux
/dev/sda3           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux

Disk /dev/sdg: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079662

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         115      923706    b  W95 FAT32
/dev/sdg2             116        9964    79112092+  83  Linux
raz@raz-desktop:~$ 
```

Yes! 
sdg is my USB hard disk. sdg1 is USB bootable Live CD of Jaunty, sdg2 is backup. I keep sdg powered down and unplugged when not needed.

sda2 and sdb1 are linux data partitions not auto mounted at boot.
sda5 is Jaunty, sda7 is Mint 5, sdb2 is Sabayon 4.1, sda4 is Windows 7 RC & sda3 is a NTFS data partition.

The only partitions auto mounting at boot are the OS I choose to boot & swap. All the other partitions are mountable from Linux.

As you cab see you can have quite a few partitions that are mountable from Linux.

---

### Post by presence1960 on 2009-08-13
use entire disk should wipe all trace of MS off your disk including MBR as GRUB will be written to MBR.

---

### Post by running_rabbit07 on 2009-08-13
> **presence1960 said:**
> The only partitions auto mounting at boot are the OS I choose to boot & swap. All the other partitions are mountable from Linux.

As you cab see you can have quite a few partitions that are mountable from Linux.

Sweet, so I just do the /, /home, and swap then make  the "backup" any format?

Thanks for the swift info. 

I never realized it but my MS files were a mess, junk everywhere with duplicates and even triplicates of folders. Not to mention having one of each Music, Pics, and Docs for all three operating systems.

---

### Post by presence1960 on 2009-08-13
> **running_rabbit07 said:**
> Sweet, so I just do the /, /home, and swap then make  the "backup" any format?

Thanks for the swift info. 

I never realized it but my MS files were a mess, junk everywhere with duplicates and even triplicates of folders. Not to mention having one of each Music, Pics, and Docs for all three operating systems.

Yepper, I keep my back ups as ext3, some prefer NTFS but then you have to deal with fragmentation. But nevertheless NTFS or even FAT will work.

---

### Post by running_rabbit07 on 2009-08-13
> **presence1960 said:**
> Yepper, I keep my back ups as ext3, some prefer NTFS but then you have to deal with fragmentation. But nevertheless NTFS or even FAT will work.

Thanks again.

Does the .Mozilla folder contain the FF bookmarks?

---

### Post by presence1960 on 2009-08-14
> **running_rabbit07 said:**
> Thanks again.

Does the .Mozilla folder contain the FF bookmarks?
 yes, your profile folder has everything you have set up in firefox. it will be named something like this ```
09egmirjf.default
```.

You can place that folder back in your .mozilla directory. if FF doesn't use that profile when you start FF, close FF and open a terminal and run ```
firefox -P
``` Choose the create profile option, follow the prompts and choose the profile folder in .mozilla you wish to use. Once the new profile has been created you can safely delete the other profile if you wish.

P.S. Thunderbird works the same way except the command to open thunderbird profile manager is > thunderbird -profilemanager

---

### Post by running_rabbit07 on 2009-08-14
Cool, Thanks for the help.

---

### Post by running_rabbit07 on 2009-08-14
Finishing up upgrades then my system will be completely functional like it was before. APTonCD makes life easier when reinstalling.

Definitely can't do a full reinstall of Windows that quick.

---

