---
title: "Common 6TB RAID10 volume for 12.04LTS and Win 8"
date: 2013-07-08
forum: Hardware
---

### Post by TheDutchman on 2013-07-08
Dear community,

For my new computer I've opted for a Linux-Windows dualboot. I use a Samsung 256GB Pro SSD for Win 8 and a OCZ Vertex 2 120GB SSD for Linux. I also have 4x WD30EFRX (RED) configured on the Intel Onboard RAID-controller as 1 single 6TB volume called "Storage". ( 
I've initialised my RAID-volume using Intel Storage Technology app in Win8 as 1 single 6TB NTFS volume. It works fast and fine, however I cannot get the volume to display/mount in my Ubuntu. 

I am using 12.04LTS with XFCE4 and Cairo-Dock+Synapse. Kernel version is 3.5.0-36-generic.
I've tried allot with dmraid and mdadm (But I think I only have to use dmraid because I'm trying to detect and not create). 
Some usefull prompts:

```
jan@jan-Z87X-UD5H:/$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"


```

```
jan@jan-Z87X-UD5H:~$ sudo fdisk -l

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30e7e9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   500115455   249698304    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 115.0 GB, 115033153536 bytes
255 heads, 63 sectors/track, 13985 cylinders, total 224674128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d187b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1       205142014   224673791     9765889    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdf2   *        2048   205139967   102568960   83  Linux
/dev/sdf5       205142016   224673791     9765888   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_bdhbggeecg_Storage-0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_bdhbggeecg_Storage-0: 801.5 GB, 801548406784 bytes
256 heads, 63 sectors/track, 97068 cylinders, total 1565524232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bdhbggeecg_Storage-0p1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/isw_bdhbggeecg_Storage-1: 801.5 GB, 801548406784 bytes
255 heads, 63 sectors/track, 97449 cylinders, total 1565524232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bdhbggeecg_Storage-1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_bdhbggeecg_Storage'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_bdhbggeecg_Storage: 1603.1 GB, 1603096805376 bytes
256 heads, 63 sectors/track, 194137 cylinders, total 3131048448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bdhbggeecg_Storage1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/isw_bdhbggeecg_Storage1: 134 MB, 134217728 bytes
255 heads, 63 sectors/track, 16 cylinders, total 262144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 48128 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bdhbggeecg_Storage1 doesn't contain a valid partition table


```

I cannot figure out why the isw_bdhbggeecg_StorageXX gets detected wrongfully ? Why 4 ? 
Even if I delete the files in /dev/mapper/ after a reboot I still get the same files.
 It is my first time using RAID and I did need a couple of tries to get it right, maybe this causes the 4 entries? 

```
jan@jan-Z87X-UD5H:~$ sudo dmraid -r
/dev/sde: isw, "isw_bdhbggeecg", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdd: isw, "isw_bdhbggeecg", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdc: isw, "isw_bdhbggeecg", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdb: isw, "isw_bdhbggeecg", GROUP, ok, 5860533166 sectors, data@ 0


```

```
jan@jan-Z87X-UD5H:~$ sudo dmraid -ay
RAID set "isw_bdhbggeecg_Storage" already active

```

```
jan@jan-Z87X-UD5H:/dev/mapper$ ls -la
total 0
drwxr-xr-x  2 root root     140 Jul  8  2013 .
drwxr-xr-x 18 root root    4880 Jul  8 16:57 ..
crw-------  1 root root 10, 236 Jul  8 16:45 control
lrwxrwxrwx  1 root root       7 Jul  8 16:57 isw_bdhbggeecg_Storage -> ../dm-2
lrwxrwxrwx  1 root root       7 Jul  8 16:45 isw_bdhbggeecg_Storage-0 -> ../dm-0
lrwxrwxrwx  1 root root       7 Jul  8 16:57 isw_bdhbggeecg_Storage1 -> ../dm-3
lrwxrwxrwx  1 root root       7 Jul  8 16:45 isw_bdhbggeecg_Storage-1 -> ../dm-1

```

When I try double-clicking "isw_bdhbggeecg_Storage" as root (sudo nautilus) I get the following error:
```
Could not display "/dev/mapper/isw_bdhbggeecg_Storage".
There is no application installed for block device files.
Do you want to search for an application to open this file?

```

I've also installed the ntfs-3g package and the NTFS Configuration Tool but I can't get things going. Any advice ?

---

### Post by TheDutchman on 2013-07-09
Ok It seems that dmraid and mdadm give conflicts when used together. mdadm is better supported by Intel and should be used. So I deleted dmraid with:
```
sudo apt-get remove --purge dmraid 
```

Now you can use mdadm to scan and assemble the existing RAID-volume using:
```
jan@jan-Z87X-UD5H:~$ sudo mdadm --assemble --scan
mdadm: Container /dev/md/imsm0 has been assembled with 4 drives
mdadm: Started /dev/md/Storage with 4 devices


```

After this my RAID-volume is vissible, Now I only need to make sure the volume is mounted everytime I boot...

EDIT:

Added to /etc/rc.local
```
mdadm --assemble --scan
```

Probably not "the" way to go, but Hey, it works ! :)

---

