---
title: "need help reasble raid 5 array"
date: 2008-07-20
forum: General Help
---

### Post by Fredrik_b on 2008-07-20
Hi after conectiong and dissconcting several IDE and onr SATA drive to my filserver running ububtu 8.04 on a raid 1 array (2x 40GB pata) and raid 5 on 4x 750B sata on a prommise fasttrack s150 tx4 controller card, may raid 5 array failed.

For some reason my raid 1 array stopped working, got it to work again by change the harddrives to my second IDE port. 

But after this my raid 5 array is dead.

If I look in "Every 2.0s: cat /proc/mdstat"
my raid 5 array look like this:

md3 : inactive sda[0](S) sdd[3](S) sdc[2](S) sdb[1](S)
      2930297856 blocks


in fdisk -l it look like this

```
administrator@server:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 15.9 GB, 15998058496 bytes
2 heads, 4 sectors/track, 3905776 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 1998 MB, 1998651392 bytes
2 heads, 4 sectors/track, 487952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 22.0 GB, 22010724352 bytes
2 heads, 4 sectors/track, 5373712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/sde: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007225f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1945    15623181   fd  Linux raid autodetect
/dev/sde2            1946        2188     1951897+  fd  Linux raid autodetect
/dev/sde3            2189        4864    21494970   fd  Linux raid autodetect

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1945    15623181   fd  Linux raid autodetect
/dev/sdf2            1946        2188     1951897+  fd  Linux raid autodetect
/dev/sdf3            2189        4864    21494970   fd  Linux raid autodetect
administrator@server:~$ 

```

for some reason md3 is gone

the correct lien is in fstab
/dev/md3 /var/media auto defaults 0 3

what has gone wrong?

---

### Post by fjgaude on 2008-07-20
/dev/md3 /var/media auto defaults 0 3

Shouldn't that "3" be a 2 or a 0?

---

### Post by Fredrik_b on 2008-07-21
No, 
md0 is my /
md1 swap
md2 /home

these 3 raid parition are on my 2 40GB drives (raid 1).

---

### Post by fjgaude on 2008-07-21
Sorry for being less than clear. The "3" is the one at the end of the line, after the "0". It should be either a 2 or a 0.

---

### Post by Fredrik_b on 2008-07-22
I I have now tried with both a 2 and a 0 with no luck. There must be some way to rectivare them, what would happend if both my system disk faild? would there still be possible to recreate the array?

---

### Post by Fredrik_b on 2008-07-22
solved it the sulution was as i suspectet a rebuild was needed and the commad to o this was:

sudo mdadm --assemble --force --scan /dev/md3

---

### Post by fjgaude on 2008-07-22
Very good! That's the normal way, not to re-build, but to assemble an array.

Glad you fixed your problem.

---

### Post by Fredrik_b on 2008-09-06
Hi, everything has worked fine for weeks, but for some reason one day I could not connect to the computer with NXclient, SSH via putty worked. This part is now solved by removing and reinstalling NXserver.

But the raid failed, I have reasebled the array with the sudo mdadm --assemble --force --scan /dev/md3 command but it only asembles 3/4 harddrives so it is in a degraded state.

How do I re add the missing drive? and how do I find out witch drive is missing?

More info belove.

> administrator@server:~$ sudo mdadm -D /dev/md3
/dev/md3:
        Version : 00.90.03
  Creation Time : Wed Jul  9 22:50:11 2008
     Raid Level : raid5
     Array Size : 2197723392 (2095.91 GiB 2250.47 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Sat Sep  6 15:16:48 2008
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e53386f5:388251a8:01f9e43d:ac30fbff (local to host server)
         Events : 0.831006

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       8       32        1      active sync   /dev/sdc
       2       8       80        2      active sync   /dev/sdf
       3       0        0        3      removed
administrator@server:~$



> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f8be10d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f8be10d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9355    75144006   83  Linux
/dev/sdb2            9356        9729     3004155    5  Extended
/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25c552f7

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd562898a

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d5663e9

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/md3: 2250.4 GB, 2250468753408 bytes
2 heads, 4 sectors/track, 549430848 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x9d5663e9

    Device Boot      Start         End      Blocks   Id  System
administrator@server:~$             

---

### Post by fjgaude on 2008-09-06
From the data it looks like it is /dev/sdd that is removed from the array.

What does

```
sudo cat /proc/mdstat
```

show?

Using fdisk -l to examine drives in an array does little good. You might try using mdadm to examine:

```
sudo mdadm -E /dev/sdd
```

Interesting you have not partitioned the drives before creating the array. You have sdc, etc., instead od sdc1. I usually make a whole-drive partition then add the drive to the create process of a new array.

The normal way to first remove a bad drive from an array is to **stop** the array, **unmount** it, then use mdadm to **fail** the drive, **remove** it, and then **add** it back in.

Most of my knowledge comes from reading, studing these:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Good luck!

---

