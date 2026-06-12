---
title: "Too Many Partitions, which ones can I get rid of?"
date: 2009-12-08
forum: Hardware
---

### Post by chiques on 2009-12-08
Hi Everyone,
I've ran into a couple of instances which called for me to reinstall Ubuntu. During the installation I unintentionally created unwanted partitions. Would anyone know which ones of these partitions I can get rid of (I'll try to figure out how later) without screwing up my Ubuntu or Windowz partitions?

> 
root@user-laptop:/home/user# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3906    31374913+   7  HPFS/NTFS
/dev/sda2            3907       12638    70139790    5  Extended
/dev/sda3           12639       14136    12032685    c  W95 FAT32 (LBA)
/dev/sda4           14463       14593     1052226   d7  Unknown
/dev/sda5            4926        5434     4088511   82  Linux swap / Solaris
/dev/sda6            5435       12638    57866098+  83  Linux
/dev/sda7            4876        4925      401593+  82  Linux swap / Solaris
/dev/sda8            3907        4875     7783429+  83  Linux

Partition table entries are not in disk order
root@user-laptop:/home/user# 





I also show this


> root@user-laptop:/home/user# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              55G   51G  1.3G  98% /
udev                  975M  212K  975M   1% /dev
none                  975M   92K  975M   1% /dev/shm
none                  975M  364K  975M   1% /var/run
none                  975M     0  975M   0% /var/lock
none                  975M     0  975M   0% /lib/init/rw
/dev/sr0              690M  690M     0 100% /media/cdrom0
root@user-laptop:/home/user# 


I have 8GB just being wasted that I would really like to recover. I would appreciate any help.

[[IMG]http://img31.imageshack.us/img31/9239/8gb.th.jpg[/IMG]](http://img31.imageshack.us/i/8gb.jpg/)

---

### Post by MyR on 2009-12-08
Well, here's the order they are on the disk:

/dev/sda1 * 1 3906 31374913+ 7 HPFS/NTFS = WINDOWS
/dev/sda2 3907 12638 70139790 5 Extended = LOGICAL PARTITION THE CONTAINS THE FOLLOWING 4 PARTITIONS {
  /dev/sda8 3907 4875 7783429+ 83 Linux
  /dev/sda7 4876 4925 401593+ 82 Linux swap / Solaris
  /dev/sda5 4926 5434 4088511 82 Linux swap / Solaris
  /dev/sda6 5435 12638 57866098+ 83 Linux = UBUNTU
  }
/dev/sda3 12639 14136 12032685 c W95 FAT32 (LBA)
/dev/sda4 14463 14593 1052226 d7 Unknown

I would delete sda3,4,7,8.  Do this at your own risk.  Make sure you backup all your data before attempting to modify partitions.

---

### Post by chiques on 2009-12-08
> **MyR said:**
> Well, here's the order they are on the disk:

/dev/sda1 * 1 3906 31374913+ 7 HPFS/NTFS = WINDOWS
/dev/sda2 3907 12638 70139790 5 Extended = LOGICAL PARTITION THE CONTAINS THE FOLLOWING 4 PARTITIONS {
  /dev/sda8 3907 4875 7783429+ 83 Linux
  /dev/sda7 4876 4925 401593+ 82 Linux swap / Solaris
  /dev/sda5 4926 5434 4088511 82 Linux swap / Solaris
  /dev/sda6 5435 12638 57866098+ 83 Linux = UBUNTU
  }
/dev/sda3 12639 14136 12032685 c W95 FAT32 (LBA)
/dev/sda4 14463 14593 1052226 d7 Unknown

I would delete sda3,4,7,8.  Do this at your own risk.  Make sure you backup all your data before attempting to modify partitions.

Hi MyR,

Thanks for the risky suggestion but I'm confused on what happens to the partition once I delete it? I've tried this before and tried to add it to my /home partition but was not able to. I would like to add it to my current /home partition but I don't know how. I booted using the live cd and if you notice (referring to my image below) the partitions are inside my sda2 partition. 

[[IMG]http://img29.imageshack.us/img29/6291/screenshotdevsdagpartedo.th.png[/IMG]](http://img29.imageshack.us/i/screenshotdevsdagpartedo.png/)

---

### Post by MyR on 2009-12-08
When you delete a partion, the space on the drive becomes "unallocated", unused and just sitting there.  You can create new partitions or move/resize existing partitions to fill the "unallocated" space.

You do not have a "/home partition".  If you did, it would have appeared in your "df -h".  So your entire Linux filesystem, including the space in your /home directory is all in one partition.

I already noted above that you have 4 partions inside your sda2 partition.  You may still edit these partitions

I can see by your screenshot that /dev/sda3 is the recovery partition installed by HP.

Hope this clears some confusion ;]

---

### Post by fancypiper on 2009-12-08
You only need one swap partition, so it would be safe to delete one of your swaps. If you do so, remember to edit /etc/fstab and delete the deleted swap.

Since it is a new installation, another possibility to consider is to re-install Ubuntu, using your preferred partitioning scheme.

---

### Post by MyR on 2009-12-08
> **fancypiper said:**
> You only need one swap partition, so it would be safe to delete one of your swaps.

Since it is a new installation, another possibility to consider is to re-install Ubuntu, using your preferred partitioning scheme.

Reinstalling is a possibility... but that's probably the last thing he wants to do now.  There's no reason he can't salvage his current installation.

One thing that I find interesting is the numbering. Judging by the partition numbers, the Ubuntu installation he is using is **not** the most recent one that was installed.  Why that is the case is something I'd like to know before suggesting anything specific to do with gparted (partition editor).

Also to be sure which swap he is using he needs to look at /etc/fstab

---

### Post by chiques on 2009-12-08
FYI, my fstab

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8a28e53b-d793-4ac5-9930-32344b64d80d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a9b32e04-b8dd-11dd-a3db-590f66130159 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


not sure which which swap I can get rid of.

Can I delete sda7 and sda8?

---

### Post by MyR on 2009-12-08
I can now be faily confident that sda5 is the swap you are using.

If I were you I would:
**Delete** sda3 sda4 sda7 and sda8 like I suggested earlier.
Optional: resize 5 to something smaller (like 2GB). I think 3.9GB for swap is ridiculous.  I have 2GB of RAM and I don't use swap at all.
I would then **move** 5 and 6 to the beginning of 2.
Next I would **resize** 2 to fill the unallocated space.
Finally I would **resize** 6 to completely fill the empty space in 2.

Make sure if have a backup of course.  It should be a fun time.  Don't panic if it takes a long time to complete.

You will probably need to update grub after you finish partitioning.

---

### Post by chiques on 2009-12-08
> **MyR said:**
> I can now be faily confident that sda5 is the swap you are using.

If I were you I would:
**Delete** sda3 sda4 sda7 and sda8 like I suggested earlier.
Optional: resize 5 to something smaller (like 2GB). I think 3.9GB for swap is ridiculous.  I have 2GB of RAM and I don't use swap at all.
I would then **move** 5 and 6 to the beginning of 2.
Next I would **resize** 2 to fill the unallocated space.
Finally I would **resize** 6 to completely fill the empty space in 2.

Make sure if have a backup of course.  It should be a fun time.  Don't panic if it takes a long time to complete.

You will probably need to update grub after you finish partitioning.


I'll back up and go for it. I predict I'll get stuck during the moving but that's just me. I'll post my status after following these suggestions.

---

### Post by chiques on 2009-12-08
> **MyR said:**
> I can now be faily confident that sda5 is the swap you are using.

If I were you I would:
**Delete** sda3 sda4 sda7 and sda8 like I suggested earlier.
Optional: resize 5 to something smaller (like 2GB). I think 3.9GB for swap is ridiculous.  I have 2GB of RAM and I don't use swap at all.
I would then **move** 5 and 6 to the beginning of 2.
Next I would **resize** 2 to fill the unallocated space.
Finally I would **resize** 6 to completely fill the empty space in 2.

Make sure if have a backup of course.  It should be a fun time.  Don't panic if it takes a long time to complete.

You will probably need to update grub after you finish partitioning.

Problem:

I'm unable to resize 2 to fill the unallocated space. I currently have about 11GB within 2 partitions that I would like to fill in sda6. I also noticed there is a hierarchy. Does that pose a problem?

Here is my updated screenshot.

[[IMG]http://img20.imageshack.us/img20/5279/screenshotdevsdagpartedp.th.png[/IMG]](http://img20.imageshack.us/i/screenshotdevsdagpartedp.png/)

I'll post the menu options in each unallocated partition in my next thread.

---

### Post by chiques on 2009-12-08
i got lost

[[IMG]http://img194.imageshack.us/img194/310/sda2menu.th.png[/IMG]](http://img194.imageshack.us/i/sda2menu.png/)


[[IMG]http://img194.imageshack.us/img194/7673/unallocsub.th.png[/IMG]](http://img194.imageshack.us/i/unallocsub.png/)


[[IMG]http://img43.imageshack.us/img43/8271/unallocupper.th.png[/IMG]](http://img43.imageshack.us/i/unallocupper.png/)

how do i fill them into sda2?

---

### Post by MyR on 2009-12-08
The keys mean they're locked because they're mounted.  Right click on sda5 and unmount it.
Are you going to remove sda3 and sda4?

You then need to right click on sda2 and resize it.

---

### Post by MyR on 2009-12-08
> **chiques said:**
> Problem:

I'm unable to resize 2 to fill the unallocated space. I currently have about 11GB within 2 partitions that I would like to fill in sda6. I also noticed there is a hierarchy. Does that pose a problem?

Here is my updated screenshot.

[[IMG]http://img20.imageshack.us/img20/5279/screenshotdevsdagpartedp.th.png[/IMG]](http://img20.imageshack.us/i/screenshotdevsdagpartedp.png/)

I'll post the menu options in each unallocated partition in my next thread.

Unless you delete 3 and 4 you don't need to resize 2 because the partitions you deleted were inside 2, therefore the unallocated space is inside 2.

---

### Post by chiques on 2009-12-08
> **MyR said:**
> Unless you delete 3 and 4 you don't need to resize 2 because the partitions you deleted were inside 2, therefore the unallocated space is inside 2.


What action should I take to merge this disk space with my 'target' partition (59GB)? I have a 10 GB and 2 GB partition.

Here's my unallocated 10GB:
[[IMG]http://img7.imageshack.us/img7/1461/10gbfree.th.png[/IMG]](http://img7.imageshack.us/i/10gbfree.png/)

Here's my 2GB unallocated space:
[[IMG]http://img268.imageshack.us/img268/373/2gbfree.th.png[/IMG]](http://img268.imageshack.us/i/2gbfree.png/)

I would like to 'merge' them into this target partition (59GB)
[[IMG]http://img268.imageshack.us/img268/1079/targetpart.th.png[/IMG]](http://img268.imageshack.us/i/targetpart.png/)

---

### Post by chiques on 2009-12-09
I got it! I was missing the fact that you have to move and stretch the target partition, not the unallocated space. I'm good now.


[[IMG]http://img24.imageshack.us/img24/4614/partitioned.th.png[/IMG]](http://img24.imageshack.us/i/partitioned.png/)


Thanks everyone for your help!!!

---

