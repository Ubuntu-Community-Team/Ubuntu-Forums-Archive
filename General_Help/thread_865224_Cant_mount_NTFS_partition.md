---
title: "Cant mount NTFS partition"
date: 2008-07-20
forum: General Help
---

### Post by RuleMaker on 2008-07-20
Something really strange happened today, i dual booting with windows xp, I have 4 partitions
1) NTFS: windows xp
2) NTFS: neutral, used by both systems
3) ext2: ubuntu hardy heron
4) swap

Since I started to use ubuntu I didn't booted into XP, i find ubuntu great.
Today I reinstalled my ubuntu and I cant mount 2) partition (the neutral one).
It says that it's using some file system that's not supported by my system (before I reinstalled it it worked).
Now I booted int the XP and I saw that ubuntu has placed it trash directory onto my F partition (2).
Note: 
-I was able to mount It once, but when I tryed to unmount it sayed:
Trash must be cleared before unmounting (or something like that).
Please help :confused:

---

### Post by tech0007 on 2008-07-20
post the output of:

sudo fdisk -l

and

cat /etc/fstab

---

### Post by drs305 on 2008-07-20
If you use UUIDs you might as well check them - the ubuntu one probably changed after the reinstall although that one should have updated itself in fstab:
```
sudo blkid
```

---

### Post by RuleMaker on 2008-07-20
fdisk -l:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef1aef1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3826        9471    45351495    f  W95 Ext'd (LBA)
/dev/sda3            9472        9964     3960022+  82  Linux swap / Solaris
/dev/sda5            3826        6375    20482843+  83  Linux
/dev/sda6            6376        9471    24868588+   7  HPFS/NTFS

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2aba0320-9d7a-42c3-9106-7582a2b5f102 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=3765c45e-0491-45ca-bd66-c06a411d3367 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Ostalo
UUID=D4307E03307DED3C /media/Ostalo ntfs-g3 auto,users,uid=1000

P.S.
I edited my fstab to mount that partition automatically on startup, It worked before reinstallation, i also used the new UUID, I don't have a cue what have gone wrong.

EDIT:
here is the exact error that I get when i try to mount that "corrupted" NTFS partition:
> The volume 'Ostalo' uses the  file system which is not supported by your system.
I booted into XP and i was able to access it.

---

### Post by drs305 on 2008-07-20
> **RuleMaker said:**
> 

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2aba0320-9d7a-42c3-9106-7582a2b5f102 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=3765c45e-0491-45ca-bd66-c06a411d3367 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Ostalo
UUID=D4307E03307DED3C /media/Ostalo **ntfs-g3** auto,users,uid=1000

P.S.
I edited my fstab to mount that partition automatically on startup, It worked before reinstallation, i also used the new UUID, I don't have a cue what have gone wrong.

EDIT:
here is the exact error that I get when i try to mount that "corrupted" NTFS partition:

I booted into XP and i was able to access it.

Change that to "**ntfs-3g**" and I think your problem will be solved.

---

### Post by RuleMaker on 2008-07-20
I mistyped it:)
This solved the mounting problem, thanks!
But why is the trash located on that partition, I mean, shouldn't it be on the file system partition?

---

### Post by drs305 on 2008-07-20
> **RuleMaker said:**
> 
But why is the trash located on that partition, I mean, shouldn't it be on the file system partition?

By default, ntfs trash does not become part of the system or user's trash. When files are deleted from an ntfs or vfat partition, they are gone for good. Normally you get a warning message saying the file will be permanently deleted and asking what you want to do.

When you include uid=1000 (and perhaps gid=1000) in fstab, the next time you boot it will create a .Trash-1000 (or whatever the gid is) on the ntfs partition. Files deleted on the ntfs partition will now go into the .Trash-1000 folder and can be recovered until the trash folder is emptied. The trash is also included in and viewable by clicking on the user's trash icon on the Desktop.

---

### Post by RuleMaker on 2008-07-20
Just as i thought, thanks for good explanation.

---

