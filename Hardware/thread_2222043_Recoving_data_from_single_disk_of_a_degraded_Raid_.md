---
title: "Recoving data from single disk of a degraded Raid 1 array."
date: 2014-05-04
forum: Hardware
---

### Post by mango.muncher2 on 2014-05-04
I have a single Sata HD that was part of a two disc Raid 1 array. The other disk of the array failed. 
The Raid was made during install of 12.04. Now running 14.04 on a fresh non raid HD.
I want to retrieve data from the degraded array.

Try to c/o simple mount:
```
andrew@Z87X-UD4H:~$ sudo mount /dev/sda2 /mnt
mount: unknown filesystem type 'linux_raid_member'
  
```


Try to assemble with mdadm:
```
andrew@Z87X-UD4H:~$ sudo mdadm --assemble /dev/sda2
mdadm: device /dev/sda2 exists but is not an md array.
```

Try to force mdadm:
```
andrew@Z87X-UD4H:~$ sudo mdadm --assemble /dev/sda2 --force
mdadm: device /dev/sda2 exists but is not an md array.

```

fdisk -l
```
andrew@Z87X-UD4H:/etc$ sudo fdisk -l
[sudo] password for andrew: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf39cdc49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sdb2          718848  1953521663   976401408    7  HPFS/NTFS/exFAT

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cce38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1      1937899518  1953523711     7812097    5  Extended
/dev/sda2   *        2048  1937897471   968947712   fd  Linux raid autodetect
/dev/sda5      1937899520  1953523711     7812096   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

In progress...........

---

### Post by mango.muncher2 on 2014-05-04
```
andrew@Z87X-UD4H:~$ sudo mdadm --query /dev/sda2
[sudo] password for andrew: 
/dev/sda2: is not an md array
/dev/sda2: device 2 in 2 device unknown raid1 array.  Use mdadm --examine for more detail.
```

```
andrew@Z87X-UD4H:~$ sudo mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3ee342a1:3f193207:cef7bed3:7625a80d
           Name : ubuntu:0
  Creation Time : Wed May 30 00:15:38 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1937893376 (924.06 GiB 992.20 GB)
     Array Size : 968946552 (924.06 GiB 992.20 GB)
  Used Dev Size : 1937893104 (924.06 GiB 992.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8ddacdef:f9b6476f:827b6558:a6122883

    Update Time : Sun May  4 06:29:27 2014
       Checksum : 95c84330 - correct
         Events : 71588
```

---

### Post by mango.muncher2 on 2014-05-04
Have already tried to assemble but thought I would try this:
```
andrew@Z87X-UD4H:~$ sudo mdadm --assemble --scan 
mdadm: /dev/md/0 has been started with 1 drive (out of 2)
```

Hmmmm

```
andrew@Z87X-UD4H:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed May 30 00:15:38 2012
     Raid Level : raid1
     Array Size : 968946552 (924.06 GiB 992.20 GB)
  Used Dev Size : 968946552 (924.06 GiB 992.20 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun May  4 06:29:27 2014
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:0
           UUID : 3ee342a1:3f193207:cef7bed3:7625a80d
         Events : 71588

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8        2        1      active sync   /dev/sda2
```

Now mount it:
```
andrew@Z87X-UD4H:~$ sudo mount /dev/md0 /mnt

```

Success.

---

### Post by raggabee on 2015-01-26
> **mango.muncher2 said:**
> Have already tried to assemble but thought I would try this:
```
andrew@Z87X-UD4H:~$ sudo mdadm --assemble --scan 
mdadm: /dev/md/0 has been started with 1 drive (out of 2)
```

Hmmmm

```
andrew@Z87X-UD4H:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed May 30 00:15:38 2012
     Raid Level : raid1
     Array Size : 968946552 (924.06 GiB 992.20 GB)
  Used Dev Size : 968946552 (924.06 GiB 992.20 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun May  4 06:29:27 2014
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:0
           UUID : 3ee342a1:3f193207:cef7bed3:7625a80d
         Events : 71588

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8        2        1      active sync   /dev/sda2
```

Now mount it:
```
andrew@Z87X-UD4H:~$ sudo mount /dev/md0 /mnt

```

Success.

Thank you so much for posting! This last command worked for me too -- just when I was starting to think I had lost my data.

---

