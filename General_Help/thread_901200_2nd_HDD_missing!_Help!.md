---
title: "2nd HDD missing! Help!"
date: 2008-08-26
forum: General Help
---

### Post by maxmanapple on 2008-08-26
After my late reboot, my 2nd HDD is missing from Places menu and from "Computer".

I want it back, what can I do to bring it back? It's a NTFS File System

---

### Post by Too Late on 2008-08-26
Go to terminal and type:
```
sudo fdisk -l
```
(the last letter is a L with small case)
```
sudo blkid
```
and
```
cat /etc/fstab
```

Post the outputs here and, if possible, tell us which one is the drive you don't see there.

---

### Post by maxmanapple on 2008-08-26
sudo fdisk -l:

```
Disk /dev/sda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6020

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2372    19053058+  83  Linux
/dev/sda2            2373        2481      875542+   5  Extended
/dev/sda5            2373        2481      875511   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
240 heads, 63 sectors/track, 10587 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x493a4d2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         666     5034928+   b  W95 FAT32
/dev/sdb2   *         667       10586    74995200    7  HPFS/NTFS

```

sudo blkid:

```
/dev/sda1: UUID="4b6d0353-c788-4545-adb6-17b9e440bf13" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="053009c6-1b1e-488d-bc08-add220fc6063" 
/dev/sdb1: LABEL="DOCUMENTOS" UUID="28DE-6683" TYPE="vfat" 
/dev/sdb2: UUID="B09012789012456E" LABEL="Downloads60" TYPE="ntfs" 
```

cat etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4b6d0353-c788-4545-adb6-17b9e440bf13 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=053009c6-1b1e-488d-bc08-add220fc6063 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /storage ntfs defaults 0 0
/dev/sdb2 /storage fat32 defaults 0 0

```

The one is missing is dev/sdb (both 1 and 2)

---

### Post by Too Late on 2008-08-26
> **maxmanapple said:**
> ```

/dev/sdb1 /storage ntfs defaults 0 0
/dev/sdb2 /storage fat32 defaults 0 0

```

Let's take a look on those lines.

At the first line, it says that the sdb1 will be mounted in the directory /storage. Do you have that directory at all? In addition, it will be mounted as a ntfs partition, althought blkid and fdisk tell us that this sdb1 is a FAT32 partition. So it won't work.

At the second line, it says that the sdb2 will be mounted in that same directory. If that directory really exists, it will be mounted "over" that sdb1 so the sdb1 would be invisible. In addition, it will be mounted as a fat32 partition, althought blkid and fdisk tell us that this sdb2 is a NTFS partition. So it won't work. In fact, that /etc/fstab file doesn't understand the word "fat32". Instead, there should be a word "vfat" when you want to mount a fat32 partition.

EDIT: So what you have to do? If you don't want them to automount (as I'm expecting, since Places and Computer show the filesystems which are not mounted), go to terminal, and type:
```
gksudo gedit /etc/fstab
```
and place a # in the beginning of those two lines. Like this:
```

# /dev/sdb1 /storage ntfs defaults 0 0
# /dev/sdb2 /storage fat32 defaults 0 0

```
This would make those lines comments, so they do nothing. (Of course, you could simply delete those two lines, it would have the same effect.)

EDIT 2: Alternatively, you can of course repair those fstab lines if you want that the drive will be automatically mounted at every boot. In this case, the lines should be something like this:
```

/dev/sdb1 /mnt/data1 vfat defaults 0 0
/dev/sdb2 /mnt/data2 ntfs defaults 0 0

```
The folders (data1 and data2) must exist. If you want to see a desktop icon, use a directory which is inside the "/media/" directory (eg. /media/data1). You may also want to change the mounting options (now "defaults").

---

### Post by maxmanapple on 2008-08-26
```
dev/sdb1 /storage/storage1 vfat defaults 0 0 
dev/sdb2 /storage/storage2 ntfs defaults 0 0
```

After this, it sill doesn't appear. I already saved the file.

What I do next?

---

### Post by Too Late on 2008-08-26
Sorry, I edited my previous post about 10 times. Notice that those folders must exist before mounting. And now there's a mistake in the very beginning of the lines. A slash is missing (should be /dev/sdb...).

When you edit the /etc/fstab file, the changes don't take effect until you reboot, OR go to terminal and type:
```
sudo mount -a
```

---

