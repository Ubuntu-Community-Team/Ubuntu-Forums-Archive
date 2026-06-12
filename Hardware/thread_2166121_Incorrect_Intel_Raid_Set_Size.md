---
title: "Incorrect Intel Raid Set Size"
date: 2013-08-07
forum: Hardware
---

### Post by Tim_Milstead on 2013-08-07
I was using Intel fake RAID on Centos 6 to store my home folders.
I've changed to Ubuntu 13.04 but I can no longer mount the RAID device and mdraid and gdisk report an incorrect raid set / device size.
The RAID is made up of two mirrored 3TB hard disk drives.

```
# dmraid -r
```

Correctly (?) reports:

> 
/dev/sdc: isw, "isw_bdfcfcaebb", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdb: isw, "isw_bdfcfcaebb", GROUP, ok, 5860533166 sectors, data@ 0


But

```
# dmraid -s
```

reports an incorrect size (actually appears to be the size of my boot disk that is a non raid volume):

> 
*** Group superset isw_bdfcfcaebb
--> Active Subset
name   : isw_bdfcfcaebb_Volume0
size   : 1565520128
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0


Which matches with what

```
# gdisk /dev/dm-0
```

(incorrectly) reports for the partition list:

> 
GPT fdisk (gdisk) version 0.8.5

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): p
Disk /dev/dm-0: 1565520136 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 883D6478-728E-4670-AA64-81CEA1CD2306
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860487134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860485119   2.7 TiB     0700  


Here is the partition information reported by ```
# cat /proc/partitions
```:

> 
major minor  #blocks  name

   8        0  732574584 sda
   8        1  669921280 sda1
   8        2   62651392 sda2
   8       16 2930266584 sdb
   8       32 2930266584 sdc
 252        0  782760068 dm-0


Which looks correct.

Is there a way of correcting the incorrect size in the raid set? I am loathed to rebuild (```
# dmraid -R
```) unless I know it is able to fix this kind of error. The BIOS utility only appears to provide destructive changes.

---

### Post by Tim_Milstead on 2013-08-08
It doesn't look like anyone knows how to rebuild the RAID. Perhaps someone know whether I can get my data off the individual disks?

It looklike like I might have to install Windows just so I can fix this which would be a bit sad.

---

