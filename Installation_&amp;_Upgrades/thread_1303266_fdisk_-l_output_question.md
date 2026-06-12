---
title: "fdisk -l output question"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by kapilajayanath on 2009-10-28
Hi,

I have the following question on the "fdisk -l" output. 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a588a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        3836       96390   83  Linux
/dev/sda3            3837       18959   121475497+  83  Linux
/dev/sda4           18960       19457     4000185    5  Extended
/dev/sda5           18960       19457     4000153+  82  Linux swap / Solaris


What is the meaning of the plus(+) sign seen on Blocks field of some of the file systems?

Thanks,
Kapila

---

### Post by efflandt on 2009-10-28
It is possible that something changed your disk geoemetry so partitions no longer fall on cylinder boundaries or not whole blocks, hence the +.  When I originally shrunk my XP Home partition sda2, ntfsresize kept cyl, head geometry like it was.  But when I first installed WinXP 64-bit beta (on sda4), it changed my heads to 255 and cylinders to match that, and XP 64 would not even boot itself (much less anything else).  I had to use fdisk from a Linux rescue CD to reconstruct my partition table without partition details written down (just some from memory in my head), so I had to experiment a bit before I got everything to boot (XP 64 on sda4 and XP home on sda2, sda1 is HP data).

When I later installed SuSE 9 on sda3 and was going to let it do its thing, I recognized that it was trying to do the same thing (change my disk geometry), so I said no, and to use sda3 as is.

When I recently installed Ubuntu on sda4, I manually just told it to format sda4 (overwriting expired XP 64 beta) and not change any partitions.  As you can see from the following, my heads are not 255 (but it was 255 after XP 64 install, and may have been if I had let newer Linux versions do their thing).  Not sure why OS's change the disk geometry, maybe so older operating systems (limited to 255 heads and 1024 cyl) can boot from more of the disk, but that can sometimes lose a little disk space or mess up existing OS's:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2             620       22600   166176360    7  HPFS/NTFS
/dev/sda3           22601       24226    12292560   83  Linux
/dev/sda4   *       24227       25841    12209400   83  Linux

---

### Post by kapilajayanath on 2009-10-29
Hi efflandt, 

Thanks a lot for the explanation. But as you can see on the my output, only my "sda1" partition doesn't end up in cylinder boundary. sda3 and sda5 partitions also showing the plus(+) sign. When I checked with "parted" command, it doesn't have any comment about cylinder boundary. Please see the output below and advice.

(parted) print                                                            
Model: ATA SAMSUNG HM160HI (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  31.5GB  31.5GB  primary   ntfs         boot 
 2      31.5GB  31.6GB  98.7MB  primary   ext4              
 3      31.6GB  156GB   124GB   primary   ext4              
 4      156GB   160GB   4096MB  extended                    
(parted) 


Thanks,
Kapila

---

### Post by mechro on 2009-10-29
Here is the output on my system of both fdisk and sfdisk. sfdisk quotes cylinders with a minus sign. It may give you a clue as to what's occurring but you may have to whip out your binary/hex calculator to pin it down exactly.

```
anthony@anthony-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+  83  Linux
/dev/sda2           13055       26108   104856255   83  Linux
/dev/sda3           26109       39162   104856255   83  Linux
/dev/sda4           39163       60801   173815267+   f  W95 Ext'd (LBA)
/dev/sda5           39163       39293     1052226   82  Linux swap / Solaris
/dev/sda6           39294       52347   104856223+  83  Linux
anthony@anthony-desktop:~$ sudo sfdisk -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  13053   13054- 104856223+  83  Linux
/dev/sda2      13054   26107   13054  104856255   83  Linux
/dev/sda3      26108   39161   13054  104856255   83  Linux
/dev/sda4      39162   60800   21639  173815267+   f  W95 Ext'd (LBA)
/dev/sda5      39162+  39292     131-   1052226   82  Linux swap / Solaris
/dev/sda6      39293+  52346   13054- 104856223+  83  Linux

```

---

