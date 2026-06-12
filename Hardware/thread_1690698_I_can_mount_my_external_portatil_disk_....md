---
title: "I can mount my external portatil disk ..."
date: 2011-02-18
forum: Hardware
---

### Post by Yajaira on 2011-02-18
My initial problem was ... I could not erease the files frome my hard external disk ... everything says Read-Only File ... so I started reading at some forums ... BUT I could not fix it. Then I found some strange files on the disc ... so I was thinking that it was a virus... so I look again on a forum and I did this ...

 dd if=/dev/zero of=/dev/sdb

And I erease EVERYTHING even though the viruses, but I lose all my files :( 

The I try to see what was on the external disc but I can see it any more ... so I put  on the terminal ...

root@Yaja:/media# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74ea74ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4980    40001818+   7  HPFS/NTFS
/dev/sda2            4981        6847    14996677+  83  Linux
/dev/sda3            6848        7096     2000092+  82  Linux swap / Solaris
/dev/sda4            7097        9729    21149572+   b  W95 FAT32

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
root@Yaja:/media# 

and now I do not understand anything ... I am SCARED :D ... because everything is going worst every minute I "try to fix this" ...

Someone could help me? Plese ... 

I do not need to say ... buy I am new on this ... have anyone noted?

Thanks

Yajaira

---

### Post by dabl on 2011-02-18
> **Yajaira said:**
> 

Disk /dev/sdb doesn't contain a valid partition table



This is the result of the "dd" command that you did. So, all your data and the partition table on that hard drive are gone now.

To make a new partition table, you need to use the program GParted.  It is found on the GParted Live CD and the Parted Magic Live CD that you can burn, or you can use a Ubuntu Live CD and run GParted.

First, choose "Device > New Partition Table" and choose "MS-DOS" as the type of partition table.

Second, right-click in the graphic of the "Unallocated Space" and choose "New > New Partition", ext4 filesystem, give it a label if you wish.

Here is guidance: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

