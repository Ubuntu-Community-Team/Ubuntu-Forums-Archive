---
title: "SATA Hard drive partitioning issues. | mdadm the cause?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Christopher Young on 2007-06-08
Hi.  I have been using k/Ubuntu for a few months (since 6.06) and I recently decided to install Ubuntu 7.04 on my main desktop, I backed up my hardware RAID on another computer and proceeded to install Ubuntu.  After installation my RAID was not detected and I can not locate a Linux driver for it.  SO I booted into BIOS and took my 2 x 250Gig RAID0 off and just decided I would use a software RAID.  Well the drives were detected, but I ran into quite a strange error:
> 
GParted 0.2.5

Format /dev/sda1 as ext3    ( ERROR )
     	
set partitiontype    ( SUCCES )
create new ext3 filesystem    ( ERROR )
     	
mkfs.ext3 /dev/sda1
     	
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda1 is apparently in use by the system; will not make a filesystem here!

========================================


After this error, I tried "sudo umount /dev/sda1" & "sudo umount /dev/sda".  It printed that the drive was not mounted on both commands.  So I went into my mtab and the drives are not listed in there.

Logically I switched to command line.
> 
christopher@cherubim:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 30515.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-30515, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-30515, default 30515): 
Using default value 30515

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
christopher@cherubim:~$ 


Next I rebooted and the drive had not taken the new partition table!

I previously attempted to make this into a RAID via mdadm and could never get it to work.  I looked into "sudo fdisk -l":
> 
christopher@cherubim:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 250.9 GB, 250994294784 bytes
2 heads, 4 sectors/track, 61277904 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4787    38451546   83  Linux
/dev/hdb2            4788        4998     1694857+   5  Extended
/dev/hdb5            4788        4998     1694826   82  Linux swap / Solaris
christopher@cherubim:~$ 

I performed "sudo mdadm --manage -r /dev/md0" and the device still shows, and the drives are still "locked".  If I perform "sudo mdadm --stop /dev/md0" it dissappears from "sudo fdisk -l", yet the drives are still locked.

Any help would be greatly appreciated.  I really need to have this issue resolved so that I may begin running this file server again.

---

### Post by daschmidty on 2007-06-08
In the end do you want to use mdadm? If so you should not try to format each physical partition as they will no longer be recognized by mdadm. You need to format md0. I've found the best way to solve a locked drive problem if you are planning to reformat anyways is to boot a gparted livecd and deleting the RAID partitions.

---

### Post by Christopher Young on 2007-06-08
> **daschmidty said:**
> In the end do you want to use mdadm? If so you should not try to format each physical partition as they will no longer be recognized by mdadm. You need to format md0. I've found the best way to solve a locked drive problem if you are planning to reformat anyways is to boot a gparted livecd and deleting the RAID partitions.

Well, yes.  I was HOPING to run it as a software RAID0.  If that is not possible I would be grateful just to have two independent 250 Gigs.

---

### Post by daschmidty on 2007-06-08
I still think your best bet may be to axe the partitions with a livecd and try to rebuild a new array and hope it works out.

---

### Post by Christopher Young on 2007-06-09
Saved myself some trouble and axed the entire installation.  Also booted into BIOS and saw I was still set on RAID, must have forgotten to save or something.  >.<

Anywho, the issue has been resolved, I now have 2 x 250Gig storage device working.  Please close.

---

