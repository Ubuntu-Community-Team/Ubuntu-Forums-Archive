---
title: "MDADM RAID5 screwy stuff"
date: 2013-05-17
forum: Hardware
---

### Post by tehtide on 2013-05-17
I've got an issue with a RAID 5 that I have. 4 disks and 1 spare for a total of 5 disks.

I've had a bit of issues with it degrading and dropping out disks and I think I've isolated that to faulty SATA cables. Right now I've got the RAID reassembled and it is in recovery mode and rebuilding.

Now for the funny stuff.

If I do a mdadm -E /dev/sd[bcdef] this is what I get:

```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri May 17 21:36:51 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 27fa9406 - correct
         Events : 11354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       8       80        3      active sync   /dev/sdf
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       48        5      spare   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri May 17 21:36:51 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 27fa9418 - correct
         Events : 11354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       8       80        3      active sync   /dev/sdf
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       48        5      spare   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri May 17 21:36:51 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 27fa942a - correct
         Events : 11354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       48        5      spare   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       8       80        3      active sync   /dev/sdf
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       48        5      spare   /dev/sdd
/dev/sde:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri May 17 21:36:51 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 27fa943e - correct
         Events : 11354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       64        4      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       8       80        3      active sync   /dev/sdf
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       48        5      spare   /dev/sdd
/dev/sdf:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri May 17 21:36:51 2013
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 27fa944c - correct
         Events : 11354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       80        3      active sync   /dev/sdf

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       8       80        3      active sync   /dev/sdf
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       48        5      spare   /dev/sdd
```

The line that is getting me is this one:
```
2     2       0        0        2      faulty removed
```

MDADM is showing the proper number of devices, but it seems to think that there is another device somewhere that it can't get to. How can I fix this? Is there a way to remove a device from the RAID via device number?

---

### Post by SaturnusDJ on 2013-05-18
Try this:
```

mdadm /dev/md0 --remove detached

```

---

### Post by tehtide on 2013-05-18
Can I do this while it is rebuilding? Do I need to stop the RAID prior to issuing the command?

Thanks for the help.

---

### Post by SaturnusDJ on 2013-05-18
Yes, it's a very safe command.

---

### Post by tehtide on 2013-05-18
Ok... ran the command but I'm still showing the faulty removed. Will it clear itself up after the rebuild it done?

---

### Post by SaturnusDJ on 2013-05-18
Okay. Maybe, I don't know.

What is the output of
```

mdadm --detail /dev/md0

```

---

### Post by tehtide on 2013-05-18
It isn't showing up in that... so maybe it will clear itself up.

Output:
```

mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Thu Jan  6 22:28:14 2011
     Raid Level : raid5
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat May 18 10:52:58 2013
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 60% complete

           UUID : 7181e53d:9d0e2322:a1dba4fa:bb34958c (local to host yoda)
         Events : 0.13555

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       5       8       48        2      spare rebuilding   /dev/sdd
       3       8       80        3      active sync   /dev/sdf
       4       8       64        4      active sync   /dev/sde

```

I'm hoping that once the rebuild gets done that it will kick that fault removed from the -E portion and I'll be all done. We'll see. I'll update once it is done. Should be later tonight. Rebuilding 8TB on an atom processor takes a while.

---

### Post by SaturnusDJ on 2013-05-18
I think it will. :)

---

### Post by tehtide on 2013-05-20
Yep... it cleared itself out.

Thanks for the help. I'm going to mark as solved.

---

