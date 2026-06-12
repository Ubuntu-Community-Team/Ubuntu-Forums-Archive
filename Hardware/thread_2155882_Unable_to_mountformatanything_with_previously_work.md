---
title: "Unable to mount/format/anything with previously working hard drive"
date: 2013-06-19
forum: Hardware
---

### Post by mmcinnis on 2013-06-19
Help, I've been banging on this for days. I re-install either 10.04 or 12.04 and Ubuntu boots fine. I pop off the cd drive and plut in the other hard drive (320gb/NTFS) and initially you can see the drive in Ubuntu but can't mount. Following the fstab and virtual drive instructions :  
 

 /dev/sdb	/mnt/D_Drive	auto	rw,auto,user,exec	0	0
 

 I attempt to mount -a  
 or
 /etc# sudo mount -t ntfs  /dev/sdb /mnt/D_Drive
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


 

 Here is what I see for disks/partitions

 

 root@crunch005:/etc# sudo fdisk -l
 

 Disk /dev/sda: 120.0 GB, 120034123776 bytes
 255 heads, 63 sectors/track, 14593 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x00000ac3
 

    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1       13995   112412672   83  Linux
 /dev/sda2           13995       14594     4805633    5  Extended
 /dev/sda5           13995       14594     4805632   82  Linux swap / Solaris
 

 Disk /dev/sdb: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x07147c7f
 

    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb2            2937       38913   288985252+   5  Extended
 /dev/sdb5            2937       38913   288985221    7  HPFS/NTFS
 

 Any help is much appreciated.
 

 Thanks in advance!

---

### Post by ahallubuntu on 2013-06-19
~

---

