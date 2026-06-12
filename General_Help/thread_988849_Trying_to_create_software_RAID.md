---
title: "Trying to create software RAID"
date: 2008-11-20
forum: General Help
---

### Post by pas_paa on 2008-11-20
Hello,

I have been trying to set up a software RAID on my Ubuntu machine (7.10). 
I have one disk for the OS and then two identical Maxtor 320GB SATA disks that I want to set up as RAID 1.

Both disks are formatted ntfs.

Output from fdisk -l
++++++++++++++++++++++++++++++++++++++++
[I]root@office:/home/bob# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac8b60f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac8b60f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe06c8ea5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2382    19133383+  83  Linux
/dev/hda2            2383        2491      875542+   5  Extended
/dev/hda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/md0: 320.0 GB, 320070221824 bytes
255 heads, 63 sectors/track, 38912 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00030f75

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       38912   312560608+  83  Linux[/I]
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

I give command:
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda /dev/sdb

followed by:
mkfs -t ntfs /dev/md0
(this one takes forever, but gives no errors once it is done)

However, when trying to mount md0, I get:
+++++++++++++++++++++++++++++++++++++++++++++++++++
[I]root@office:/home/bob# mount -t ntfs /dev/md0 /media/store
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

root@office:/home/bob# mount -t ntfs /dev/md0p1 /media/store
Failed to access '/dev/md0p1': No such file or directory[/I]
+++++++++++++++++++++++++++++++++++++++++++++++++++

I tried to use GParted to create a partition, but I get this error:

++++++++++++++++++++++++++++++++++++++++++++++++++++++
[I]GParted 0.3.3

Libparted 1.7.1

Format /dev/md0p1 as ntfs  00:01    ( ERROR )
     	
calibrate /dev/md0p1  00:01    ( SUCCES )
     	
path: /dev/md0p1
start: 63
end: 625121279
size: 625121217 (298.08 GiB)
set partitiontype on /dev/md0p1  00:00    ( SUCCES )
     	
new partitiontype: ntfs
create new ntfs filesystem  00:00    ( ERROR )
     	
mkntfs -Q -vv /dev/md0p1
     	
The device doesn't exist; did you specify it correctly?[/I]
++++++++++++++++++++++++++++++++++++++++++++++++++++++

Any help would be greatly appreciated.

---

