---
title: "Trouble with mdadm raid 0 array"
date: 2016-02-15
forum: Hardware
---

### Post by pulseplanet on 2016-02-15
Hello All

   I created a raid array with 4 drives, and one of them failed. So I recreated it with the 3 good ones. 
   Recently, after a reboot, I could no longer assemble them. The raid0 was created on a CentOS system, but I am trying to rescue and mount them on ubuntu 14.04

   Here is what I tried so far:

```
  dev > fdisk -l

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x23992cc0

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1915781119 1915779072 913.5G 83 Linux
/dev/sda2       1915783166 1953523711   37740546    18G  5 Extended
/dev/sda5       1915783168 1953523711   37740544    18G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1           1 4294967295 4294967295   2T ee GPT

Partition 2 does not start on physical sector boundary.


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

```

```
dev > cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 15 Feb 2016 00:38:55 -0600
# by mkconf $Id$

```


```
dev > mdadm --assemble --scan --verbose 
mdadm: looking for devices for further assembly
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdd is identified as a member of /dev/md/imsm0, slot -1.
mdadm: /dev/sdc is identified as a member of /dev/md/imsm0, slot -1.
mdadm: /dev/sdb is identified as a member of /dev/md/imsm0, slot -1.
mdadm: added /dev/sdc to /dev/md/imsm0 as -1
mdadm: added /dev/sdb to /dev/md/imsm0 as -1
mdadm: added /dev/sdd to /dev/md/imsm0 as -1
mdadm: Container /dev/md/imsm0 has been assembled with 3 drives
mdadm: looking for devices for further assembly
mdadm: looking for devices for further assembly
mdadm: /dev/sdd is busy - skipping
mdadm: /dev/sdc is busy - skipping
mdadm: /dev/sdb is busy - skipping
mdadm: no recogniseable superblock on /dev/sda5
mdadm: Cannot assemble mbr metadata on /dev/sda2
mdadm: no recogniseable superblock on /dev/sda1
mdadm: Cannot assemble mbr metadata on /dev/sda
mdadm: looking in container /dev/md/imsm0
mdadm: found match on member /md127/0 in /dev/md/imsm0
mdadm: array /dev/md/data2_0 now has 3 devices
mdadm: looking for devices for further assembly
mdadm: /dev/sdd is busy - skipping
mdadm: /dev/sdc is busy - skipping
mdadm: /dev/sdb is busy - skipping
mdadm: looking in container /dev/md/imsm0
mdadm: member /md127/0 in /dev/md/imsm0 is already assembled

```


```
dev > mdadm --examine /dev/md/imsm0
/dev/md/imsm0:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : 2259a8ea
         Family : 2259a8ea
     Generation : 00000084
     Attributes : All supported
           UUID : 29618c02:1007417b:0bb7631c:8eb0a858
       Checksum : fe2b2672 correct
    MPB Sectors : 2
          Disks : 4
   RAID Devices : 1

  Disk01 Serial : S1E1C63L
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[data2]:
           UUID : 4366f5bf:9fb03815:927aa42a:a7756cae
     RAID Level : 0
        Members : 4
          Slots : [UU_U]
    Failed disk : none
      This Slot : 1
     Array Size : 14846783488 (7079.50 GiB 7601.55 GB)
   Per Dev Size : 3711696136 (1769.87 GiB 1900.39 GB)
  Sector Offset : 0
    Num Stripes : 28997624
     Chunk Size : 64 KiB
       Reserved : 0
  Migrate State : idle
      Map State : failed
    Dirty State : clean

  Disk00 Serial : S240SZ66
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk02 Serial : S1E19XBJ:0
          State : active
             Id : ffffffff
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk03 Serial : S1E19YY9
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

```


```

dev > ls /dev/md*
/dev/md126  /dev/md127

/dev/md:
imsm0

```

```

dev > mdadm -D /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 3

Working Devices : 3


           UUID : 29618c02:1007417b:0bb7631c:8eb0a858
  Member Arrays : /dev/md126

    Number   Major   Minor   RaidDevice

       0       8       32        -        /dev/sdc
       1       8       16        -        /dev/sdb
       2       8       48        -        /dev/sdd

```

```

dev > mdadm -I -e imsm /dev/md127
dev > 

```

```

dev > mkdir /temp127 ; mount -t ext4 /dev/md127 /temp127
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

```

dev > mkdir /temp126 ; mount -t ext4 /dev/md127 /temp126
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

```

dev > cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdd[2](S) sdb[1](S) sdc[0](S)
      9459 blocks super external:imsm
       
md126 : inactive sdb[2] sdc[1] sdd[0]
      5567544192 blocks super external:/md127/0
       
unused devices: <none>

```


Any help in getting this array mounted would help. Thanks.

---

### Post by TheFu on 2016-02-16
What file system do the RAID have?  Was LVM used?

---

### Post by pulseplanet on 2016-02-26
> **TheFu said:**
> What file system do the RAID have?  Was LVM used?

Ext4

No LVM

---

### Post by TheFu on 2016-02-26
After you created the array,  assembled it, then was an ext4 file system built (using mkfs)?
Everything was working on the CentOS box with 3 disks? Yes?

I've never created RAID directly on disks - we always create a huge partition for the drive first. Read that in a best practice guide somewhere. Prevents someone uninitiated from accidentally assuming a RAID disk is empty.

Probably not much help.  Never had this issue, but I've never used RAID0 either.

---

### Post by drave40 on 2016-02-27
check out this page or google imsm0

[http://serverfault.com/questions/226053/intel-matrix-storage-raid-and-linux-mdadm](http://serverfault.com/questions/226053/intel-matrix-storage-raid-and-linux-mdadm)

---

### Post by pulseplanet on 2016-02-29
> **drave40 said:**
> check out this page or google imsm0

[http://serverfault.com/questions/226053/intel-matrix-storage-raid-and-linux-mdadm](http://serverfault.com/questions/226053/intel-matrix-storage-raid-and-linux-mdadm)

Thanks for that link. I did see it before posting my question. The trouble is I still do not see the /dev/md126p1 device (which I used to see before with just mdadm --assemble --scan). After the reboot /dev/md126p1 seems to have just vanished.

```
root@T55:/# mdadm -I /dev/md/imsm0 
root@T55:/# ls /dev/md*
/dev/md126  /dev/md127
```

---

