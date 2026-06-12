---
title: "ubuntu partition not getting detected , shown as 0 size in fdisk in live cd"
date: 2010-04-18
forum: Hardware
---

### Post by abhaythewinner on 2010-04-18
I initially had ubuntu 9.10 installed . I then installed windows xp in a different partition . Then fixed the grub thing again.
Now problem is that my ubuntu partition is not being detected . When I boot through a live cd , the ubuntu partition does not show up and output of fdisk command shows it a zero size

My harddisk is 80 GB with partitions of size 37 GB , 25 GB , 200 MB and 15 GB . 15 GB partition contains ubuntu which is not detected now and boot partition is 200 MB one.


ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeff6eff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS
/dev/sda2        78140160   156296384    39078112+   f  W95 Ext'd (LBA)
/dev/sda3        78140286   126977759    24418737    7  HPFS/NTFS
/dev/sda4       126977823   127379384      200781   83  Linux
/dev/sda5        78140161    78140161           0    0  Empty

Disk /dev/sdb: 2051 MB, 2051013632 bytes
64 heads, 62 sectors/track, 1009 cylinders, total 4005886 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d31a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     4003711     2001825    b  W95 FAT32




ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78140097, Id= 7, bootable
/dev/sda2 : start= 78140160, size= 78156225, Id= f
/dev/sda3 : start= 78140286, size= 48837474, Id= 7
/dev/sda4 : start=126977823, size=   401562, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       62, size=  4003650, Id= b, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0





ubuntu@ubuntu:~$ sudo parted  /dev/sda print
Error: Can't have overlapping partitions.              



Here /dev/sdb is my pendrive containg live ubuntu OS.

Plz help me recover the ubuntu partition . As it has some very documents in it.

---

### Post by srs5694 on 2010-04-18
It appears that your extended partition (/dev/sda2) overlaps two of your primary partitions (/dev/sda3 and /dev/sda4). Your /dev/sda5 is only one sector long. Your valid partitions are:


[list]
[*]/dev/sda1 -- 37GiB NTFS
[*]/dev/sda3 -- 23GiB NTFS
[*]/dev/sda4 -- 196MiB Linux
[/list]


I can find no trace of the 15GB Ubuntu partition, although there is 13.8GiB of unpartitioned space at the end of the disk. (Note: I'm using "GB" to mean 10^9 bytes and "GiB" to mean 2^30 bytes.)

I recommend you delete /dev/sda5 and /dev/sda2, then run testdisk to attempt to locate and recover the lost Linux partition.

If testdisk fails, you might be able to recover the partition by blindly creating a new partition at the end of the disk; however, it's unclear if it was originally primary or logical. Try creating a primary partition first, and if that fails, you could try creating a new extended partition and a new logical partition inside it. Note that creating a logical partition in that space will necessarily write one sector's data in the currently-unallocated space, which could be damaging if it's not the right thing to do. (That why I suggested creating the primary partition first; this action alone won't write anything to the unallocated space.)

---

### Post by abhaythewinner on 2010-04-19
@srs5694
thanx for you pointing me in right direction...
it did not delete partitions but used testdisk.
It showed my lost ubuntu partition . I wrote that partition table to disk . I have got my ubuntu back 
but windows installation has corrupted now. The disk where windows was installed is showing strange 1-2 GB files. 
Can you help if this can be corrected?

---

