---
title: "Cannot undelete ext2 partition using TestDisk"
date: 2008-08-24
forum: General Help
---

### Post by LennyCZ on 2008-08-24
Hi all!

  I have a problem. I did some rearrangements with my partition table, and - as usually :-) - I ended up with errors in it. In such cases, TestDisk booted from System Rescue CD ([http://www.sysresccd.org/](http://www.sysresccd.org/)) usually saves me, but this time I cannot get one partition recovered.

This is what I do:

I let TestDisk do a "Deeper Search" to locate possible partitions. It lists all "guesses" of possible partition.

From this list, I mark primary partitions with P, logical with L and deleted/incorrect with D. (If I am unsure, I check them by listing "/" contents.)

But there's still one partition, which I know it IS correct (I can list and browse its contents in TestDisk), I also know it is logical one, but i cannot mark it as logical!!! If I press <Left> and <Right>, I can cycle through "*", "P" and "D", but "L" is just missing - with no explanation!

I am pretty confused because I have no idea why TestDisk just won't let me recover this partition.

I hope any one can help me.

Thank You in advance!!!



Here is the TestDisk guesses table:

The partition which I cannot recover is the 9th one, called [fedora8-usr] (I have my /usr on it).

```

   D HPFS - NTFS              0   1  1   521 254 63    8385867 [Serghey_WinXP]
     NTFS, 4293 MB / 4094 MiB
   D HPFS - NTFS              0   1 11   521 254 63    8385857
     NTFS found using backup sector!, 4293 MB / 4094 MiB
   D HPFS - NTFS            522   0  1   652 254 63    2104515 [WinXP_Swap]
     NTFS, 1077 MB / 1027 MiB
   D HPFS - NTFS            537   0  1   667 254 63    2104515 [WinXP_Swap]
     NTFS, 1077 MB / 1027 MiB
   D HPFS - NTFS            653   0  1  1174 254 63    8385930 [WinXP_c-PF]
     NTFS, 4293 MB / 4094 MiB
   * Linux Swap            1175   2  1  1304 254 63    2088324
     SWAP2 version 1, 1069 MB / 1019 MiB
   D Linux                 1306   0  1  1549 254 63    3919860 [fedora8-usr]
     EXT2 Large file Sparse superblock, 2006 MB / 1913 MiB
   D Linux                 1306   1  1  1958 254 63   10490382 [debian]
     EXT3 Large file Sparse superblock, 5371 MB / 5122 MiB
   P Linux                 1959   0  1  2741 254 63   12578895 [fedora8-usr]
     EXT2 Large file Sparse superblock, 6440 MB / 6142 MiB
   L HPFS - NTFS           2742   1  1  2933 254 63    3084417 [MoVE]
     NTFS, 1579 MB / 1506 MiB
   L HPFS - NTFS           2934   1  1  3188 254 63    4096512 [droot]
     NTFS, 2097 MB / 2000 MiB
   D FAT32 LBA             3189   1  1  6509 254 63   53351802 [D-PUB]
     FAT32, 27 GB / 25 GiB
   D HPFS - NTFS           3191   1  1  6509 254 63   53319672
     NTFS found using backup sector!, 27 GB / 25 GiB
   L FAT32 LBA             6510   1  1  8694 254 63   35101962 [D-LENNYCZ]
     FAT32, 17 GB / 16 GiB
   D Linux                 9060   1  1  9712 254 63   10490382
     EXT3 Large file Sparse superblock, 5371 MB / 5122 MiB
   D HPFS - NTFS           9060   1  6  9712 254 63   10490377
     NTFS found using backup sector!, 5371 MB / 5122 MiB
   D Linux                 9076   1  1  9728 254 63   10490382
     EXT3 Large file Sparse superblock Recover, 5371 MB / 5122 MiB
   D FAT32 LBA             9713   1  1  9728 254 63     256977 [SERGHEY_1XN]
     FAT32, 131 MB / 125 MiB
```

Here is some fdisk output (the partition is not shown here as it seems "deleted"):

```
# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         522     4192933+   7  HPFS/NTFS
/dev/sda2             523         653     1052257+   7  HPFS/NTFS
/dev/sda3             654        1175     4192965    7  HPFS/NTFS
/dev/sda4            1176        9729    68710005    f  W95 Ext'd (LBA)
/dev/sda5            1176        1305     1044162   82  Linux swap / Solaris
/dev/sda6            1307        1959     5245191   83  Linux
/dev/sda7            2743        2934     1542208+   7  HPFS/NTFS
/dev/sda8            2935        3189     2048256    7  HPFS/NTFS
/dev/sda9            3190        6510    26675901    c  W95 FAT32 (LBA)
/dev/sda10           6511        8695    17550981    c  W95 FAT32 (LBA)
/dev/sda11           9061        9713     5245191   83  Linux




# fdisk -ul

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8385929     4192933+   7  HPFS/NTFS
/dev/sda2         8385930    10490444     1052257+   7  HPFS/NTFS
/dev/sda3        10490445    18876374     4192965    7  HPFS/NTFS
/dev/sda4        18876375   156296384    68710005    f  W95 Ext'd (LBA)
/dev/sda5        18876501    20964824     1044162   82  Linux swap / Solaris
/dev/sda6        20980953    31471334     5245191   83  Linux
/dev/sda7        44050293    47134709     1542208+   7  HPFS/NTFS
/dev/sda8        47134773    51231284     2048256    7  HPFS/NTFS
/dev/sda9        51231348   104583149    26675901    c  W95 FAT32 (LBA)
/dev/sda10      104583213   139685174    17550981    c  W95 FAT32 (LBA)
/dev/sda11      145548963   156039344     5245191   83  Linux
```

---

