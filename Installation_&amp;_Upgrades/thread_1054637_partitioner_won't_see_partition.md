---
title: "partitioner won't see partition"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by doglover56 on 2009-01-29
Hi. I want to install Ubuntu 8 to my second hard drive. There are 6 logical partitions in one extended partition. sdb5 has 10G in it. It is FAT32. It can be seen by windows, partition magic, gparted, cfdisk. But the partitioner won't see it. Actually, more precisely the partitioner actually offers a guided choice to resize sdb5 and install to it. But when I go to manual partitioning, sdb5 is not on the list. Strange. Actually, I don't want to install to that particular partition, but since the partitioner is not seeing it I am afraid something is wrong and it will mess up. 
Anyone understand this behavior?
Thanks,
IMF

---

### Post by lisati on 2009-01-29
> **doglover56 said:**
> Hi. I want to install Ubuntu 8 to my second hard drive. There are 6 logical partitions in one extended partition. sdb5 has 10G in it. It is FAT32. It can be seen by windows, partition magic, gparted, cfdisk. But the partitioner won't see it. Actually, more precisely the partitioner actually offers a guided choice to resize sdb5 and install to it. But when I go to manual partitioning, sdb5 is not on the list. Strange. Actually, I don't want to install to that particular partition, but since the partitioner is not seeing it I am afraid something is wrong and it will mess up. 
Anyone understand this behavior?
Thanks,
IMF

About the only things that come to mind at the moment is if the partition wasb't cleanly "unmounted" by the last OS to access it, or that something odd is happening with the partition table. Anyone else?

---

### Post by tommcd on 2009-01-30
Since /dev/sdb5 can be seen by GParted, use the GParted live CD to format the partition as ext3. You will also need a swap partition also. The swap can be 512mb-1GB. You could go with less swap if you have a lot of memory. After formatting /dev/sdb5 as ext3 boot up the Ubuntu live CD and see if it sees the partition. If that does not work, use the GParted live CD and delete the partition and then recreate it in the newly created free space as a ext3 partition + a swap partition. 
Ubuntu should easily see a fat32 partition though. Try booting up the Ubuntu live CD, open a terminal (applications > accessories > terminal) and run:
```
sudo fdisk -lu
```
This will list all the partitions on your hard drives.

---

### Post by doglover56 on 2009-01-30
I will put below the fdisk -lu results from Ubuntu 6 and Ubuntu 8. Please note as review that Ubuntu 6 (with drives as hda and sdc) works fine on this P3 Dell 4100 PC, but Ubuntu 8 (with drives as sda and sdc) do not as I have inquired on prior messages, with no resolution. The immediate problem is that the partitioner in any version of Ubuntu 8, Xubuntu 8, including alternate, will not see sdc5 even though fdisk and all other manner of things see it. It had been suggested that h(s)da would not work because it has too many partitions on it, with SCSI having a limit of 15. I am not sure that is true, but then I wonder why fdisk lists all 22 partitions. Does it have its own disk access? Well anyhow, I thought then I would install on the second drive, with only a few partitions, but it still does not read the drive correctly. So, below are the v6 hd and v8 sd outputs. They look identical to me.

Thanks in advance
IMF

--------------------------------------

v6

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63      176714       88326   1b  Hidden W95 FAT32
/dev/hda2          224910    24515189    12145140   17  Hidden HPFS/NTFS
/dev/hda3   *    24563385    36853109     6144862+   c  W95 FAT32 (LBA)
/dev/hda4        36853110   117226304    40186597+   f  W95 Ext'd (LBA)
/dev/hda5        36853173    40949684     2048256    b  W95 FAT32
/dev/hda6        40949748    41062139       56196    6  FAT16
/dev/hda7        41062203    51311609     5124703+   b  W95 FAT32
/dev/hda8        51311673    53367929     1028128+   b  W95 FAT32
/dev/hda9        53367993    55424249     1028128+   b  W95 FAT32
/dev/hda10       55424313    57480569     1028128+   b  W95 FAT32
/dev/hda11       57480633    59536889     1028128+   b  W95 FAT32
/dev/hda12       59536953    71826614     6144831    b  W95 FAT32
/dev/hda13       71826678    75923189     2048256   1b  Hidden W95 FAT32
/dev/hda14       75923253    79007669     1542208+   7  HPFS/NTFS
/dev/hda15       79007733    80084024      538146    7  HPFS/NTFS
/dev/hda16       80084088    90333494     5124703+   b  W95 FAT32
/dev/hda17      100583028   102044879      730926   82  Linux swap / Solaris
/dev/hda18      102044943   106928639     2441848+  83  Linux
/dev/hda19      106928703   109274129     1172713+  83  Linux
/dev/hda20      109274193   114157889     2441848+  83  Linux
/dev/hda21      114157953   116503379     1172713+  83  Linux
/dev/hda22      116503443   117226304      361431   83  Linux

Disk /dev/hdc: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40021632 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1           16065    38074049    19028992+   f  W95 Ext'd (LBA)
/dev/hdc5           16128    21848399    10916136    b  W95 FAT32
/dev/hdc6        21848463    27712124     2931831   83  Linux
/dev/hdc7        27712188    28692089      489951   83  Linux
/dev/hdc8        28692153    30250394      779121   82  Linux swap / Solaris
/dev/hdc9        30250458    36114119     2931831   83  Linux
/dev/hdc10       36114183    38074049      979933+  83  Linux

----------------

v8

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f05b0d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   1b  Hidden W95 FAT32
/dev/sda2          224910    24515189    12145140   17  Hidden HPFS/NTFS
/dev/sda3   *    24563385    36853109     6144862+   c  W95 FAT32 (LBA)
/dev/sda4        36853110   117226304    40186597+   f  W95 Ext'd (LBA)
/dev/sda5        36853173    40949684     2048256    b  W95 FAT32
/dev/sda6        40949748    41062139       56196    6  FAT16
/dev/sda7        41062203    51311609     5124703+   b  W95 FAT32
/dev/sda8        51311673    53367929     1028128+   b  W95 FAT32
/dev/sda9        53367993    55424249     1028128+   b  W95 FAT32
/dev/sda10       55424313    57480569     1028128+   b  W95 FAT32
/dev/sda11       57480633    59536889     1028128+   b  W95 FAT32
/dev/sda12       59536953    71826614     6144831    b  W95 FAT32
/dev/sda13       71826678    75923189     2048256   1b  Hidden W95 FAT32
/dev/sda14       75923253    79007669     1542208+   7  HPFS/NTFS
/dev/sda15       79007733    80084024      538146    7  HPFS/NTFS
/dev/sda16       80084088    90333494     5124703+   b  W95 FAT32
/dev/sda17      100583028   102044879      730926   82  Linux swap / Solaris
/dev/sda18      102044943   106928639     2441848+  83  Linux
/dev/sda19      106928703   109274129     1172713+  83  Linux
/dev/sda20      109274193   114157889     2441848+  83  Linux
/dev/sda21      114157953   116503379     1172713+  83  Linux
/dev/sda22      116503443   117226304      361431   83  Linux

Disk /dev/sdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40021632 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065    38074049    19028992+   f  W95 Ext'd (LBA)
/dev/sdb5           16128    21848399    10916136    b  W95 FAT32
/dev/sdb6        21848463    27712124     2931831   83  Linux
/dev/sdb7        27712188    28692089      489951   83  Linux
/dev/sdb8        28692153    30250394      779121   82  Linux swap / Solaris
/dev/sdb9        30250458    36114119     2931831   83  Linux
/dev/sdb10       36114183    38074049      979933+  83  Linux

---

### Post by tommcd on 2009-01-30
It looks like fdisk sees all the partitions correctly. I don't know why the partitioner in Ubuntu 8.x won't see them.

Have you tried partitioning and formatting the drive the way you want with GParted live CD first, and then booting up the Ubuntu 8.x live CD and installing to the partition you want?

Or delete the partition(s) and recreate them with GParted, and then install Ubuntu to the newly created partitions?

Just out of curiosity, have you tried the Ubuntu 8.x alternate install CD? It is a shot in the dark, but I wonder if you would have better luck with the alternate install CD.

---

### Post by avtolle on 2009-01-30
From memory, only 15 partitions will be seen by the Linux operating system, even though more exist. Anyone with more knowledge, please feel free to correct me.

---

### Post by doglover56 on 2009-01-31
Hello. 
1. If linux will only see 15 scsi partitions, then why is fdisk seeing all of them?
2. This is consistent with different utilities having different behavior. fdisk will see a sda23 and/or create a sda23, but mkfs won't format an sda23. Similarly, the partitioner will see or create it, but crashes at the format stage. Also, the partitioner puts little exclamation points next to them, and can't read their filesystem.
3. The behavior is the same whether using alternate or regular disks, and whether Ubuntu 7 or 8, since both use sda will Ubuntu 6 uses hda.
4. Even with that, I am not sure why the troubles on the first disk are causing me not to see the first partition on the second disk.

Thanks,
Irwin

---

