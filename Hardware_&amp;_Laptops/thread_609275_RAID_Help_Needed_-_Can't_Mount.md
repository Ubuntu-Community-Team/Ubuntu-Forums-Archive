---
title: "RAID Help Needed - Can't Mount"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by jkzubu on 2007-11-10
I have my music and video library on a RAID and Ubuntu sees the volume but can't mount it.  I transfered this volume from Win XP (as NTFS), where it was originally set up, so I know it works there.  Upon startup, my RAID Card is recognized as: PDC20371 (FastTrak S150 TX2plus) and the volume appears to be properly recognized and assigned.  I just can't mount the volume(s).  The attachment indicates the mount problem. 

My fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=0f97a6ac-ae76-44b3-9d4b-2973223f9e96 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=f843d577-a12a-4791-907c-87c0f1658547 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /dev/disk/by-id auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0


And dmraid returned the following:

root@jimx2-desktop:/home/jimx2# dmraid -ay
RAID set "pdc_dgbhgghi" already active
RAID set "pdc_dgbhgghi1" already active
root@jimx2-desktop:/home/jimx2# dmraid -s
*** Active Set
name   : pdc_dgbhgghi
size   : 1562845184
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

root@jimx2-desktop:/home/jimx2# dmraid -r
/dev/sdb: pdc, "pdc_dgbhgghi", stripe, ok, 781422592 sectors, data@ 0
/dev/sdc: pdc, "pdc_dgbhgghi", stripe, ok, 781422592 sectors, data@ 0
root@jimx2-desktop:/home/jimx2# 

Finally, my fdisk -l is:

root@jimx2-desktop:/home/jimx2# fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d86ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c440388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       97282   781417633+  42  SFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/dm-0: 800.1 GB, 800176734208 bytes
255 heads, 63 sectors/track, 97282 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c440388

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1       97282   781417633+  42  SFS

Disk /dev/dm-1: 800.1 GB, 800171656704 bytes
255 heads, 63 sectors/track, 97281 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


So the 2 400's as RAID run fine on the XP system, but won't mount in Gutsy.  Looks like a partition table error??  Any help appreciated.


My setup:
AMD64 X2
Asus M2N-SLI Deluxe / 2GB / 250GB HD
Western Digital Serial ATA RAID controller (PCI / 2 Ports) (FastTrack S150)
2 - 400GB Western Digital SATA150 Drives set as one 800 GB 
Gutsy AMD64

Thanks.

---

