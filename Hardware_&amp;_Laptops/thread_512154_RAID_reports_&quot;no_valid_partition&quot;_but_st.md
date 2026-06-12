---
title: "RAID reports &quot;no valid partition&quot; but still boots?"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by bsmith1051 on 2007-07-28
I've got Ubuntu 7.04 running on a machine with 3 hard-drives.  The first two are installed as a RAID-1 mirror, while the 3rd is a new  'data' drive.  Ever since I installed the 3rd drive, I've been getting a "serious" error on reboot yet the computer seems to work fine.  So I suspect that I configured the 3rd drive wrong?

HOW I SETUP NEW DRIVE
```
- used gparted to create ext partition w 'ext3' drive
- checked to see ID of new drive/partition (it was /dev/hdb5)
 > sudo fdisk -l
- created mount point and did manual test mount
 > sudo mkdir /data
 > sudo mount -t ext3 /dev/hdb5 /data
- edited start-up options
 > gksudo gedit /etc/fstab
  added another line,
  /dev/hdb        /data   ext3	defaults     0       3
```

When I reboot now, the new drive is not mounted automatically so I know I did something wrong.  But before Ubuntu finishes loading, it reports some major 'fsck' error which I have no idea how to check or fix.  Instead, I just press CTRL-D to continue and Ubuntu seems to load-up fine.  

There's one other suspicious thing.  If I run 'mdadm --query --detail /dev/md0' is reports no problems.  But if I run 'sudo fdisk -l' it reports:
```
Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241    5  Extended
/dev/hdb5               1       14593   117218209+  83  Linux

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  fd  Linux raid autodetect
/dev/sda2            1217        1945     5855692+  fd  Linux raid autodetect
/dev/sda3            1946       19452   140624977+  fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  fd  Linux raid autodetect
/dev/sdb2            1217        1945     5855692+  fd  Linux raid autodetect
/dev/sdb3            1946       19457   140665140   fd  Linux raid autodetect

Disk /dev/md0: 10.0 GB, 10001842176 bytes
2 heads, 4 sectors/track, 2441856 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

**Disk /dev/md0 doesn't contain a valid partition table**

Disk /dev/md1: 5996 MB, 5996150784 bytes
2 heads, 4 sectors/track, 1463904 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 143.9 GB, 143999893504 bytes
2 heads, 4 sectors/track, 35156224 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table
```
Is this an actual problem with my RAID paritions?  Or does fdisk simply not recognize 'md' paritions correctly?  Can someone maybe help me get my 3rd drive to mount correctly, and then we'll see if the fsck 'error' goes away...

---

### Post by bsmith1051 on 2007-07-28
Nevermind....

As I was reviewing what I'd just posted, I realized the new 'fstab' entry specified the drive but not the partition, e.g. it said "hdb" but not "hdb5".  So I updated that and rebooted and now the error is gone.  So the startup error must've been from that setup error, not anything actually wrong with my RAID partitions.  Hopefully?!

---

