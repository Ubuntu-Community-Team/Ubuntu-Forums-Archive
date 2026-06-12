---
title: "Unable to mount XP drive after hibernation"
date: 2008-08-05
forum: General Help
---

### Post by sting14ray on 2008-08-05
I have a dual boot system with XP SP3 and Hardy.  I was using XP for some work, and then hibernated it.  I accidentally booted into Hardy later and tried to access some files on my XP/NTFS partition.  It then gave me a "Cannot Mount Volume: You are not privileged to mount this volume" error message.  I went back to XP, finished my work, and restarted a couple times.  I got the same message when I tried to go from Ubuntu again, so I ran checkdisk from XP.  It had to correct some index entries (add and delete), but Hardy is still giving the same message.

Output of "sudo fdisk -l" :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1317    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1318       14266   104012842+   f  W95 Ext'd (LBA)
/dev/sda4           14267       14594     2620416   dd  Unknown
Partition 4 does not end on cylinder boundary.
/dev/sda5            1318        9603    66557263+   7  HPFS/NTFS
/dev/sda6   *        9604       14070    35881146   83  Linux
/dev/sda7           14071       14266     1574338+  82  Linux swap / Solaris

output of "cat /etc/fstab" :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=24ae0377-f70e-49a0-b86b-8dc588f9d9a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=3fa30de3-e1a7-49da-abd7-747f9954e29b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


#I added this line so it automatically mounts the windows
#partition
/dev/sda5       /media/disk     ntfs-3g  defaults           0       2


I have a primary XP partition (sda5 I think), a Dell Recovery Partition (sda4??), and a Dell Mediadirect (sda3??), along with the Linux and Swap partition.  Can anyone confirm these and what sda2 is?

System:
Dell Inspiron 1520
Core 2 Duo T7300 (2.0 GHz)
2 GB RAM
120 GB HDD
nVidia GeForce 8400 GS (128 MB)

Thanks everyone.

---

### Post by Mgiacchetti on 2008-08-05
I ran into a problem mounting usb devices after hibernation.

File a bug report.

---

### Post by sayakb on 2008-08-05
Suppose you are trying to mound /dev/sda2, then at a terminal, do:
```
sudo mkdir /media/disk
sudo mount /dev/sda2 /media/disk -o force
```
That should mount the drive.

---

### Post by sting14ray on 2008-08-06
I heard some people on other forums mention using "blkid"

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-070B" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="EABA4770BA4737F9" LABEL="RECOVERY" 
/dev/sda4: LABEL="MEDIADIRECT" UUID="4A50-5487" TYPE="vfat" 
/dev/sda5: TYPE="ntfs" UUID="5E804F0E804EEC59" 
/dev/sda6: UUID="24ae0377-f70e-49a0-b86b-8dc588f9d9a9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="3fa30de3-e1a7-49da-abd7-747f9954e29b"
```


Also I ran ntfsfix /dev/sda5:

```
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

```

I had run chkdsk from XP before, and it added and deleted some stuff, should I run it again?

ntfs-3g doesn't let me select any of the ntfs drives when I run ntfs-3g config.

---

### Post by sting14ray on 2008-08-11
From what else I can gather, I have to make the NTFS partion clean somehow, or a "clean dismount", does anyone know how to do that?

Thanks.

---

### Post by nortexoid on 2009-05-02
> **sayakb said:**
> Suppose you are trying to mound /dev/sda2, then at a terminal, do:
```
sudo mkdir /media/disk
sudo mount /dev/sda2 /media/disk -o force
```
That should mount the drive.

This worked. Not only did it mount the drive, but automounting works again. Thanks!

---

