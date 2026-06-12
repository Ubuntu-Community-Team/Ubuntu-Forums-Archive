---
title: "raid controller problems?"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by xnszxdotnet on 2008-02-01
My box sees the controller shown here:
```

booger@services:~$ lspci
...
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0c.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
...

```

...but it doesn't see all the drives. I have 2x 500gb sata drives and 2x 750gb sata drives. the 320gb drive is the main OS drive:

```

booger@services:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38643   310399866   83  Linux
/dev/sda2           38644       38913     2168775    5  Extended
/dev/sda5           38644       38913     2168743+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007b6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```


...so I try to put a filesystem on one of the drives it does see and:

```

booger@services:~$ sudo mkfs.ext3 /dev/sdd
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdd is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
91586560 inodes, 183143646 blocks
9157182 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
5590 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir 
```

then I check to see if it worked:

```

booger@services:~$ sudo fdisk -l
[sudo] password for booger:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38643   310399866   83  Linux
/dev/sda2           38644       38913     2168775    5  Extended
/dev/sda5           38644       38913     2168743+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007b6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

```

and the drive is gone... what is going on? all my drives are new, so there shouldn't be any drive failures. what am I missing here? i would like to set up a RAID5 on both sets of drives. please help me.

---

### Post by xnszxdotnet on 2008-02-04
anyone??

---

### Post by xnszxdotnet on 2008-02-05
humm... guess no has had these problem

---

