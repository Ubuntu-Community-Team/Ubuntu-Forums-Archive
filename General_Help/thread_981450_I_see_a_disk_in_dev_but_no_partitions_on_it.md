---
title: "I see a disk in /dev/ but no partitions on it"
date: 2008-11-13
forum: General Help
---

### Post by panfist on 2008-11-13
It seems that the disk randomly became of type "mdraid." The details are below. I didn't figure out about the type until about the 7th post.

Basically fdisk tells me that there is /dev/sda1 as an ntfs partition. blkid, however, tells me that there is only /dev/sda and it is of type mdraid. there is no /dev/sda1. This drive was working and pulled from a windows machine. I successfully mounted it in ubuntu to transfer things from it to a RAID array, transferred half my files and then rebooted. Now I can't mount the ntfs volume anymore.

In here I explain exactly what was going on the last time when I rebooted.
[http://ubuntuforums.org/showthread.php?t=980828](http://ubuntuforums.org/showthread.php?t=980828)

//

I am having a puzzling issue with one of my hard drives. Since the last time I rebooted the partition has kind of disappeared. I have a 1TB drive with an NTFS partition that takes up the whole thing. fdisk confirms this when I print the partition table for this drive, yet in /dev/ I can only see /dev/sda ... and not /dev/sda1.

output from "sudo mount /dev/sda1 /media/ntfs"
```
$ sudo mount /dev/sda1 /media/ntfs
mount: special device /dev/sda1 does not exist
```

output from "fdisk -l" -- this shows /dev/sda1 as an ntfs partition.
```
$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002e05d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x047373ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24546   197165713+  83  Linux
/dev/hda2           24547       24792     1975995   82  Linux swap / Solaris
```

output from sudo blkid -- this shows no sda1 partition but a disk of type mdraid instead.
```
$ sudo blkid
dev/hda1: UUID="8fe9563e-ef33-4ebf-827e-0baa694f662b" TYPE="ext3" 
dev/hda2: TYPE="swap" UUID="5af15454-3332-4a4e-9886-f14bd8539b2e" 
dev/sda: UUID="17cb9058-611d-b7ae-24bf-68e341ce0fbd" TYPE="mdraid" 

```

output from "cat /etc/fstab" -- this is even more bizarre because this time I rebooted and ubuntu detected my root drive as /dev/hda1 even though no physical connections changed, whereas the file still has it as /dev/sde1.
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=8fe9563e-ef33-4ebf-827e-0baa694f662b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde2
UUID=5af15454-3332-4a4e-9886-f14bd8539b2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Please help. Thanks.

---

### Post by taurus on 2008-11-13
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by panfist on 2008-11-13
/etc/fstab seems weird because it's mount /dev/sde1 and /dev/sde2 which also don't exist in /dev...I do however see /dev/hda1 and /dev/hda2.

```
$ sudo fdisk -l

see OP
```

```
$ cat /etc/fstab

seoo OP
```

---

### Post by taurus on 2008-11-13
What is the error message when you run these commands from a terminal, especially the second one?

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```
Bet it will complain about you didn't shut it down cleanly the last time you use it.  Therefore, you have to use the force option to mount it.

---

### Post by panfist on 2008-11-13
I wish it were that simple.

```
$ sudo mount /dev/sda1 /media/ntfs
mount: special device /dev/sda1 does not exist

```

---

### Post by taurus on 2008-11-13
How about

```
sudo blkid
```

---

### Post by panfist on 2008-11-13
Ahh this is interesting:

```
/$ sudo blkid
/dev/hda1: UUID="8fe9563e-ef33-4ebf-827e-0baa694f662b" TYPE="ext3" 
/dev/hda2: TYPE="swap" UUID="5af15454-3332-4a4e-9886-f14bd8539b2e" 
/dev/sda: UUID="17cb9058-611d-b7ae-24bf-68e341ce0fbd" TYPE="mdraid"
```

edit: i was messing around with RAID arrays the other day but I definitely did NOT manually change the type of this disk. it was not even plugged in when the arrays were created. I plugged it in afterwards to transfer data from it to the array. the array ran into some weird errors and the next time I reboot, I get this disk as an mdraid for no reason (that i can find).

here's a thread that details what happened during my last reboot:
[http://ubuntuforums.org/showthread.php?t=980828](http://ubuntuforums.org/showthread.php?t=980828)

---

### Post by panfist on 2008-11-14
Bump because I added some info to the OP.

---

