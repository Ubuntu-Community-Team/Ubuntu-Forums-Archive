---
title: "Scary Fdisk Output"
date: 2013-02-04
forum: Hardware
---

### Post by Baudzilla on 2013-02-04
I have a fakeRAID 0 array of 2 160GB SATA drives which is configured through my BIOS.  The only partitioning tools I've used are GParted and the Ubuntu 12.10 installer.

Here's a list of my **primary** partitions on the RAID array:

[LIST]
[*]~240GB NTFS (Windows)
[*]~70GB ext4 (Ubuntu 12.10)
[*]4GB linux-swap
[/LIST]
The system seems to be working alright, but the output from the fdisk command makes me worry.  sda/sdb are my individual hard drives, /dev/mapper/nvidia_cdjbbejb is my 320GB RAID device, and /dev/mapper/nvidia_cdjbbejb[1-3] are my partitions on the RAID.  Here is the output from fdisk:
```


root@A8N-E:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5e295e29

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005af8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   471375871   235686912    7  HPFS/NTFS/exFAT
/dev/sdb2       471375872   617163007    72893568   83  Linux
/dev/sdb3       617163008   625163519     4000256   82  Linux swap / Solaris

Disk /dev/mapper/nvidia_cdjbbejb: 320.1 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625163520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x0005af8a

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cdjbbejb1   *        2048   471375871   235686912    7  HPFS/NTFS/exFAT
/dev/mapper/nvidia_cdjbbejb2       471375872   617163007    72893568   83  Linux
/dev/mapper/nvidia_cdjbbejb3       617163008   625163519     4000256   82  Linux swap / Solaris

Disk /dev/mapper/nvidia_cdjbbejb1: 241.3 GB, 241343397888 bytes
255 heads, 63 sectors/track, 29341 cylinders, total 471373824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cdjbbejb1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p4      2692939776  2692991410       25817+   0  Empty

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_cdjbbejb2: 74.6 GB, 74643013632 bytes
255 heads, 63 sectors/track, 9074 cylinders, total 145787136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_cdjbbejb2 doesn't contain a valid partition table

Disk /dev/mapper/nvidia_cdjbbejb3: 4096 MB, 4096262144 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8000512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x50e6b6ec

Disk /dev/mapper/nvidia_cdjbbejb3 doesn't contain a valid partition table


```Anyone know what to make of this?  Is it something I shouldn't worry about?  Should I be trying something to fix it?

---

### Post by tgalati4 on 2013-02-04
Neither fdisk nor gparted/parted support RAID, so don't expect them to properly enumerate your RAID drives.

---

### Post by Baudzilla on 2013-02-06
Thanks!  I guess I'll find an app which supports RAID so I can check my partitions then.

---

### Post by tgalati4 on 2013-02-06
```
man mdadm
```  

I don't use mdadm, since I have hardware RAIDs running, but there are lots of smart folks that know their way around mdadm.  Search the forums for "mdadm check disk".

---

