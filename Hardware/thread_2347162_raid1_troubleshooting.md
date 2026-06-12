---
title: "raid1 troubleshooting"
date: 2016-12-22
forum: Hardware
---

### Post by tomisenbaert2 on 2016-12-22
Hi there,

I recently wanted to update ubuntu-10.04 LTS server to 16.04...
Because I didn't want to update in steps to 16.04 i did a fresh install...

Though...my 10.04 had raid1 (to identical 500 GB disks)

Installation succeeded but now I'm left with a working 16.04 on a harddrive (sda) on another 10.04 on the other harddrive (sdb).
I forgot about the raid1 on installation and got stuck with raid1 with sda being removed and sdb still active synced.

I just want to disconnect sdb from the raid1 and reformat it again to put it in raid1 again with 16.04...how can I do this?

Thanks

tom@beethoven:~$ **sudo mdadm --detail /dev/md1**
/dev/md1:
        Version : 0.90
  Creation Time : Thu Mar 24 14:28:07 2011
     Raid Level : raid1
     Array Size : 480468928 (458.21 GiB 492.00 GB)
  Used Dev Size : 480468928 (458.21 GiB 492.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Dec 21 16:25:02 2016
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : ff4fdb67:78c4253f:1cc03a9f:c5993095
         Events : 0.3474

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2

tom@beethoven:~$ **sudo fdisk -l**

Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4937231f

Apparaat   Op.   Start     Einde  Sectoren   Size Id Type
/dev/sda1  *      2048    999423    997376   487M 83 Linux
/dev/sda2      1001470 976771071 975769602 465,3G  5 uitgebreid
/dev/sda5      1001472 976771071 975769600 465,3G 8e Linux LVM


Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009c73a

Apparaat   Op.    Start     Einde  Sectoren   Size Id Type
/dev/sdb1          2048  15624191  15622144   7,5G fd Linux raidautodetectie
/dev/sdb2  *   15624192 976562175 960937984 458,2G fd Linux raidautodetectie


Disk /dev/md1: 458,2 GiB, 492000182272 bytes, 960937856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


tom@beethoven:~$ **sudo cat /proc/mdstat**
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[1]
      480468928 blocks [2/1] [_U]

unused devices: <none>

---

