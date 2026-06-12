---
title: "Trouble Mounting FAT32 Partition after editing fstab"
date: 2008-10-13
forum: General Help
---

### Post by nomizzz on 2008-10-13
I edited my fstab file in order to have Ubuntu mount my fat32 sda2 partition automatically on startup.  Unfortunately, when I navigate to media/sda2 (the mount directory I specified in fstab) I find an empty directory with 6.3 gb free, a totally arbitrary number considering I have about 12 gb free on all of my partitions.  Even worse, when I try to mount any of my non-linux partitions, it gives me an arbitrary error message "Cannot Mount Volume," even when I sudo open nautilus and mount it that way.

Here's the contents of my original fstab file prior to editing:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=af7266a6-4a3d-45e9-809e-f657707b99c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d497c124-9f94-41dc-bab6-1b1563b75878 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

And here is the newly modified fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=af7266a6-4a3d-45e9-809e-f657707b99c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d497c124-9f94-41dc-bab6-1b1563b75878 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=48E4-1AD3	/media/sda2	fat32	defaults	0	0
```

Please note that "48E4-1AD3" is the UUID of the hard drive I would like to mount.  I have already tried saying /dev/sda2 instead place of that UUID number.

Thanks in advance for any advice anyone can offer.

---

### Post by mrowth on 2008-10-13
> **nomizzz said:**
> UUID=48E4-1AD3	/media/sda2	fat32	defaults	0	0
This may not relate to your immediate troubles, but isn't the file system type supposed to be "vfat", not "fat32"?

---

### Post by Patb on 2008-10-14
Nomizzz, the edit seems wrong. Open a terminal and post the output of the following commands and someone should be able to help you:
```
sudo fdisk -l
sudo blkid
```
Cheers, Pat.

---

### Post by nomizzz on 2008-10-21
Output for fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97419741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5639    45295236    7  HPFS/NTFS
/dev/sda2            7099        9729    21133507+   b  W95 FAT32
/dev/sda3            5640        6855     9767520   83  Linux
/dev/sda4            6856        7098     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Output for sudo blkid:

```
/dev/sda1: UUID="2A47735170BB2C67" TYPE="ntfs" 
/dev/sda2: UUID="48E4-1AD3" TYPE="vfat" 
/dev/sda3: UUID="af7266a6-4a3d-45e9-809e-f657707b99c4" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="d497c124-9f94-41dc-bab6-1b1563b75878" 
```

---

### Post by nomizzz on 2008-10-21
Well I feel silly, changed the filesystem to vfat and it mounts successfully.

Another question I have is whether it's a bad practice if I hibernate my windows OS, boot into Ubuntu, and then edit files on the shared partition while Windows XP hibernates.  I lost a few important files when Windows ran random ckdsk and I thought there might be some connection.

Thanks so much for the help guys.

---

### Post by vanadium on 2008-10-21
Indeed you should not mount an ntfs partition of a Windows system that is in hibernation. I am actually surprised that such a drive is being mounted for you. My understanding was that Ubuntu would not automatically mount ntfs drives that are not properly closed.

---

