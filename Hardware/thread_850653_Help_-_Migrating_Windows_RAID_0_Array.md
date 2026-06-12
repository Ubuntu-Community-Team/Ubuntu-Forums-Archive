---
title: "Help - Migrating Windows RAID 0 Array"
date: 2008-07-05
forum: Hardware
---

### Post by ToxicBomber on 2008-07-05
Here is my story so far...

Making the move to Linux with my new rig, and decided to bring over my RIAD 0 from my old WinXP machine. I created the RAID 0 using the Syba SD-SATA-4P card running the sil3114 chip. Worked flawlessly in windows after the driver was installed. Its a 2x250GB SATA RAID 0 with plenty of data I would like to keep, already on it.

Running Ubuntu 8.04 recognizes all disks but these two, or at least like it should. Gparted shows the two RAID disks as a single disk...of unallocated space. 

I don't want to have to wipe this drive just to get it useable

I would like to get the RAID mounted with all the data intact, and yes it is an NTFS formatted disk.

If someone thinks the solution is still out on the rest of the forums, please tell me to keep looking. Otherwise a hint in the right direction would be greatly appreciated.

If you want to know anything else about my setup that might help, please ask, at this point I'm willing to try anything short of wiping the drives.

*EDIT*
Well seeing as I have scoured the forums and bumped this article once already without a single helpful reply, I can only assume that at this time my plan is not feasible. Thanks to SoftRAID being a total fubar situation when it comes to Ubuntu, I am now going to purchase a second 500GB drive and drag all the info over to that one in Windows.

My experience with Ubuntu this time around has been great except for this situation. I will continue with my endeavour, and maybe look into solving this myself someday.

---

### Post by ToxicBomber on 2008-07-06
Well I poked around in the BIOS and found that its onboard RAID was in fact NOT enabled. So I fixed that and made sure to tell it which disks were part of a RAID 0. The POST message screen displayed the RAID 0 as a 500GB Stripped drive.

However it is still not recognized by Ubuntu, seen by Gparted as unallocated space...

Ran fdisk and got this HUGE mess o' output:

> Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ab83ab8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74b49ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        5226        5226           0   3b  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2           40723      279905  1921229923    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3               1           1           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4          104369      104369           0   94  Amoeba BBT
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002d002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488392033+   7  HPFS/NTFS

Disk /dev/dm-0: 500.1 GB, 500118585344 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74b49ff8

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *        5226        5226           0   3b  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2           40723      279905  1921229923    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/dm-0p3               1           1           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/dm-0p4          104369      104369           0   94  Amoeba BBT
Partition 4 does not end on cylinder boundary.

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5dac5da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30400   244187968+   7  HPFS/NTFS

---

