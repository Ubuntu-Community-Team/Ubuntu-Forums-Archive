---
title: "RAID 5 array missing"
date: 2015-04-09
forum: Hardware
---

### Post by ignaheyns on 2015-04-09
Hi,

I have an array with 4x drives, drive number 4 failed and I replaced it and started rebuilding the array.

After a while the rebuilding process stopped with an error :I/O error

Nothing responded anymore so I did a reboot of the server. After the reboot mdadm does not detect that the 4x drives are part of an array anymore.

Output of cat /proc/mdstat:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md124 : inactive sdd4[5](S) sdc4[6](S) sde4[7](S) sdb4[4](S)
      7803208448 blocks super 1.2

md125 : active (auto-read-only) raid1 sdc2[1] sdd2[2] sde2[3] sdb2[0]
      1044800 blocks [4/4] [UUUU]

md126 : active (auto-read-only) raid1 sdd3[2] sdc3[1] sde3[3] sdb3[0]
      521408 blocks [4/4] [UUUU]

md127 : active (auto-read-only) raid1 sdc1[2] sdd1[1] sde1[3] sdb1[0]
      1043840 blocks [4/4] [UUUU]


```

The array I'm interested in is md124

So when I run "mdadm --examine /dev/sd[dceb]4" it shows all 4x drives are marked as "Spare"

```
/dev/sdb4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 377e8542:6cf8ad2e:c6d37003:908c1fec
           Name : 3
  Creation Time : Fri Apr  1 23:04:32 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3901604224 (1860.43 GiB 1997.62 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 645afa0c:657018b9:27fcaab8:5da7563a

    Update Time : Thu Apr  9 09:30:25 2015
       Checksum : 360e3f8d - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
/dev/sdc4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 377e8542:6cf8ad2e:c6d37003:908c1fec
           Name : 3
  Creation Time : Fri Apr  1 23:04:32 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3901604224 (1860.43 GiB 1997.62 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 676d87fc:cb862a90:e0575c63:4092599e

    Update Time : Thu Apr  9 09:30:25 2015
       Checksum : b61af95 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
/dev/sdd4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 377e8542:6cf8ad2e:c6d37003:908c1fec
           Name : 3
  Creation Time : Fri Apr  1 23:04:32 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3901604224 (1860.43 GiB 1997.62 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : bf7f64f7:636c9f3d:fbbb5894:c87643f9

    Update Time : Thu Apr  9 09:30:25 2015
       Checksum : 3f99f027 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
/dev/sde4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 377e8542:6cf8ad2e:c6d37003:908c1fec
           Name : 3
  Creation Time : Fri Apr  1 23:04:32 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3901604224 (1860.43 GiB 1997.62 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 0c9776e3:da800342:0a14cf4c:4b4b8076

    Update Time : Thu Apr  9 09:30:25 2015
       Checksum : 65c3487e - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)


```

EDIT: Here is the "cat /proc/mdstat" from before the reboot"
```

md125 : active raid5 sdc4[6](F) sdd4[5] sdb4[4] sde4[7](S)
      5852406336 blocks super 1.2 level 5, 64k chunk, algorithm 2 [4/2] [U_U_]



```

They're not supposed to be spare, they are all part of a RAID 5 array.

How do I tell mdadm that these drives are part of an array? I really need to get the data off the array so running in degraded mode is fine, as long as I can get the data from it.

Any ideas?

---

### Post by ignaheyns on 2015-04-09
UPDATE: Okay I was able to get the drives back in a RAID configuration (sort of) using this handy thread : [http://ubuntuforums.org/showthread.php?t=1986488](http://ubuntuforums.org/showthread.php?t=1986488) 

Problem is that mdadm is not assembling the drives in the correct order.

When I run the command : 
```

mdadm --create /dev/md127 -v -l 5 -n 4 -c 64 /dev/sdb4 /dev/sdc4 /dev/sdd4 /dev/sde4



```

It's supposed to add the drives in this fashion:
Disk 0 = sdb4
Disk 1 = sdc4
Disk 2 = sdd4
Disk 3 = sde4

However when I check the status the assignments are:
```


    Number   Major   Minor   RaidDevice State
       0       8       68        0      active sync   /dev/sde4
       1       8       20        1      active sync   /dev/sdb4
       2       8       52        2      active sync   /dev/sdd4
       4       8       36        3      spare rebuilding   /dev/sdc4


```

So it assigns:
Disk 0 = sde4
Disk 1 = sdb4
Disk 2 = sdd4
Disk 3 = sdc4

In this configuration I will not be able to mount the partition.

How can I force mdadm to follow the drive assignments I specify to it?

---

### Post by ignaheyns on 2015-04-09
Okay I was able to fix the issue by running:

mdadm -S /dev/md127

and then the mdadm --create command again

Now I just need to figure out why it can't access the volume...

---

