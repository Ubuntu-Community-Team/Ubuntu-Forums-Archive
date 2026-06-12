---
title: "mdadm + re-install"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by marcovanb on 2009-09-07
Hi,

I have a media server (mythbuntu) that originally had 8.10 installed. I upgraded it through the updates. I have been unhappy with this due to some issues and want to do a reinstall with mythbuntu 9.04.

With this system I had two 200gb drives and two 1tb drives. Both are in a mirror, using mdadm, though one of the 200gb drives needs replacing. So I have two questions.

1 - If I rebuild the system with one 200gb hard drive can I at a later date add another hard drive using mdadm, to provide redundancy, even though it is the bootable drive?

2 - How can I re-add my 1tb mdadm mirror to the new OS without losing data?

Any Help would be greatly appreciated

Nick

Output from parted

[INDENT] (parted) print all                                                        
Model: ATA WDC WD2000JS-00M (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags     
 1      32.3kB  196GB  196GB   primary   ext3         boot, raid
 2      196GB   200GB  4047MB  extended                         
 5      196GB   200GB  4047MB  logical   linux-swap   raid      


Model: ATA WDC WD10EACS-00D (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  1000GB  1000GB  extended                    
 5      64.5kB  1000GB  1000GB  logical   ext3              


Model: ATA WDC WD10EACS-00D (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  1000GB  1000GB  extended                    
 5      64.5kB  1000GB  1000GB  logical   ext3              


Model: Unknown (unknown)
Disk /dev/md2: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ext3              


Model: Unknown (unknown)
Disk /dev/md0: 196GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  196GB  196GB  ext3              


Error: /dev/md1: unrecognised disk label
[/INDENT]
Output from mdadm

[INDENT]nmagers@jupiter:~$ sudo mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Feb 20 21:11:28 2009
     Raid Level : raid1
     Array Size : 191406336 (182.54 GiB 196.00 GB)
  Used Dev Size : 191406336 (182.54 GiB 196.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep  8 06:54:40 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 2b6e7717:60a1aa02:1b3645e8:3093a15c
         Events : 0.1323553

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        1        1      active sync   /dev/sda1

nmagers@jupiter:~$ sudo mdadm --misc --detail /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Fri Feb 20 21:11:50 2009
     Raid Level : raid1
     Array Size : 976759872 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976759872 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Tue Sep  8 06:55:19 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : f5bfef27:77448d0b:ced7eae6:ea2af11e
         Events : 0.218

    Number   Major   Minor   RaidDevice State
       0       8       21        0      active sync   /dev/sdb5
       1       8       37        1      active sync   /dev/sdc5
[/INDENT]

---

