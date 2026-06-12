---
title: "NTFS Drives with MDADM... Nightmare! Please Help!"
date: 2008-10-25
forum: General Help
---

### Post by Ghetek on 2008-10-25
Hi everybody,

So here is what my setup used to be. I was testing out MDADM software raid and i created a raid0 with 2 750gb hard drives. The drives were formatted to NTFs because i thought it was necessary at the time.... big mistake.

Whenever i run the command that i used to mount with i get the following error:

```
root@LNX:/# ntfs-3g /dev/md0 /mnt/storage0
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
root@LNX:/#
```

trying to mount it using "mount" gets the same results...


If i run the "MDADM --detail --scan" this is what i get:

```
root@LNX:/# mdadm --detail --scan
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=7cfc0c5c:849a2038:33a6fde4:739b09b9
root@LNX:/#
```

If i run the "mdadm --detail /dev/md0" this is what i get:

```
root@LNX:/# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Aug 12 01:00:08 2008
     Raid Level : raid0
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct 23 19:05:44 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 4K

           UUID : 7cfc0c5c:849a2038:33a6fde4:739b09b9 (local to host LNX)
         Events : 0.35

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
root@LNX:/# root@LNX:/# mdadm --detail --scan
```

I totally realize that formatting this thing into ntfs was a bad idea and as soon as its up and running in intend on moving it to an xfs raid5.

Any help would be greatly appreciated, the files on this raid are very important to me.

---

### Post by Ghetek on 2008-10-25
FOUND THE FIX!! all i had to do was run:

```
ntfsfix /dev/mdo
```

followed by:

```
ntfs-3g /dev/mdo /mnt/storage0
```

---

### Post by santhony on 2008-10-25
LOOKING FOR ADVICE.  

My Raid 5 has failed due to a Power Supply issue.  I'm unable to repair or assemble my array.  I haven't tried much in fear of damaging my set further.

Here's what I have.

santhony@ubuntu:~$ sudo mdadm --detail /dev/md0
[sudo] password for santhony: 
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.
santhony@ubuntu:~$ 

santhony@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.
santhony@ubuntu:~$ 

santhony@ubuntu:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sdb1 /dev/sdf1 /dev/sdd1 /dev/sde1 /dev/sda1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted

Now for exaimine, I get similiar output for all drives except sda1.

santhony@ubuntu:~$ sudo mdadm --examine /dev/sda1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: No md superblock detected on /dev/sda1.

I receive similar output of this from drives SDB1, SDD1, SDE1 and SDF1:

santhony@ubuntu:~$ sudo mdadm --examine /dev/sdb1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
  Creation Time : Mon Jul 14 15:01:56 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Oct 23 01:01:51 2008
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 8473b682 - correct
         Events : 741092

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       17        4      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8        1        1      active sync
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       8       17        4      active sync   /dev/sdb1
   5     5       8       81        5      spare   /dev/sdf1



PLEASE HELP...

---

### Post by santhony on 2008-10-25
Here's the EXAMINE from the Other Drives:

santhony@ubuntu:~$ sudo mdadm --examine /dev/sdd1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
  Creation Time : Mon Jul 14 15:01:56 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Oct 23 06:56:32 2008
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 847409e6 - correct
         Events : 741106

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8        1        1      active sync
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       81        5      spare   /dev/sdf1
santhony@ubuntu:~$ sudo mdadm --examine /dev/sde1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
  Creation Time : Mon Jul 14 15:01:56 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Oct 23 06:56:32 2008
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 847409fa - correct
         Events : 741106

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8        1        1      active sync
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       81        5      spare   /dev/sdf1
santhony@ubuntu:~$ sudo mdadm --examine /dev/sdf1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 67350c39:89f0ac91:0f5b4e61:2c17f314
  Creation Time : Mon Jul 14 15:01:56 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Oct 23 06:56:32 2008
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 84740a0a - correct
         Events : 741106

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       81        5      spare   /dev/sdf1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8        1        1      active sync
   2     2       8       65        2      active sync   /dev/sde1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       81        5      spare   /dev/sdf1

---

### Post by santhony on 2008-10-25
MORE INFO:

santhony@ubuntu:~$ sudo cat /proc/mdstat  Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdd1[0](S) sdf1[5](S) sdb1[4](S) sde1[2](S)
      1953535744 blocks

---

