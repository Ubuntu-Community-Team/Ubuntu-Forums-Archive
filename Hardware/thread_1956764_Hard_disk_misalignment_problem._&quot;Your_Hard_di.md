---
title: "Hard disk misalignment problem. &quot;Your Hard disk is Misaligned by 512 bytes.&quot;"
date: 2012-04-11
forum: Hardware
---

### Post by AliSajidImami on 2012-04-11
Hello all.
I am working on a new Dell N4050 laptop. This laptop came preinstalled with ubuntu 10.10 which i upgraded to 11.10 now.

My hard disk suddenly gave signs of Imminent Failure.

I ran the fdisk -lu command. Here's the output.

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1baf0215

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2           81920    10567679     5242880    b  W95 FAT32
/dev/sda3   *    10567680   616949759   303191040   83  Linux
/dev/sda4       616951806   625141759     4094977    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       616951808   625141759     4094976   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4193 MB, 4193255424 bytes
255 heads, 63 sectors/track, 509 cylinders, total 8189952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7a42275d

```

My Hard Disk is a 320 GB WD Hard Drive. It's model is "WDC WD3200BPVT-75JJ5T0".

Also the hard disk has increased Reallocated Sector Count, which jumped suddenly.

Is there any way I can recover from this error without repartiotioning?
I don't want to lose my data.

---

### Post by oldfred on 2012-04-11
The mis-alignment issue would apply if you have a newer drive with 4K sectors or a SSD. Older drives it does not really matter. Drives have been partitioned by cylinders starting at sector 63. But cylinders have not been used since hard drives went over 8GB and BIOS converted to LBA or large block allocation. 

Partition tools were updated to stop using cylinders and to align better for 4K or SSDs. 
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)


But your issue on Reallocated Sector Count and Imminent Failure are more of a concern that re- alignment will not fix. It sounds like drive is just failing. If not well backed up, back up what you can before drive totally stops.

If failure from  Disk Utility, and the report on Smart Status?

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for other Debian installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

---

### Post by gordintoronto on 2012-04-23
Your hard drive is failing, back up now!

---

