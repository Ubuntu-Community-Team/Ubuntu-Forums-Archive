---
title: "Problem mounting raid disk"
date: 2009-09-13
forum: Hardware
---

### Post by David Lindh on 2009-09-13
Hello,
I have a problem with my external network disk. Yesterday it stopt working completly and im trying to recover the data from the disks.

The device have used nraid system.

I have tried google the problem but realized that every case is different from mine in some way.

I was talking to a friend with more knowledge than me and he was helping me collect this data to help solving the problem.

```
david@david-desktop:~$ sudo mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c542bda8:b8b1eef0:3ad3f1e4:0e5968ad
  Creation Time : Tue Dec  2 10:31:54 2008
     Raid Level : linear
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Tue Dec  2 10:31:54 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2b85807 - correct
         Events : 1

       Rounding : 64K

      Number   Major   Minor   RaidDevice State
this     0       3        3        0      active sync

   0     0       3        3        0      active sync
   1     1       3       67        1      active sync

```

```
david@david-desktop:~$ sudo mdadm --assemble --run --uuid c542bda8:b8b1eef0:3ad3f1e4:0e5968ad /dev/sdb3
mdadm: no devices found for /dev/sdb3

```

```
david@david-desktop:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives.
mdadm: failed to add 8:19 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from 0 drives - not enough to start the array.

```

```
david@david-desktop:~$ sudo ls -la /dev/| grep "sd"
brw-rw----   1 root   disk      8,   0 2009-09-13 19:26 sda
brw-rw----   1 root   disk      8,   1 2009-09-13 19:26 sda1
brw-rw----   1 root   disk      8,   2 2009-09-13 17:26 sda2
brw-rw----   1 root   disk      8,   3 2009-09-13 19:26 sda3
brw-rw----   1 root   disk      8,   5 2009-09-13 19:26 sda5
brw-rw----   1 root   disk      8,  16 2009-09-13 19:26 sdb
brw-rw----   1 root   disk      8,  17 2009-09-13 19:26 sdb1
brw-rw----   1 root   disk      8,  18 2009-09-13 19:26 sdb2
brw-rw----   1 root   disk      9, 127 2009-09-13 18:15 sdb3
brw-rw----   1 root   disk      8,  20 2009-09-13 19:26 sdb4
```

---

