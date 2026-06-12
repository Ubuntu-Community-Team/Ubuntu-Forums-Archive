---
title: "Hard drive is in an &quot;unrecognizable file system&quot;"
date: 2010-11-03
forum: Hardware
---

### Post by btsgreg on 2010-11-03
I unplugged my hard drive for a few days and when I plugged it back in, I get this message:

[http://img835.imageshack.us/img835/1157/10188738.jpg](http://img835.imageshack.us/img835/1157/10188738.jpg)

Is there anyway to change the hard drive's file system without formating the drive? Data-recovery software recovers data from way back when, and nothing recent.

I'm using Windows 7 and the hard drive is a Seagate Baracuda. I've tried using the chkdsk command, but chkdsk doesn't work on RAW drives.

Any ideas?

---

### Post by dabl on 2010-11-03
Well .... {suspense building ....} .... what is that mystery filesystem?

In Ubuntu Linux, you can open a terminal and issue 

```
sudo fdisk -lu
``` 

and it should show up.  Also

```
sudo blkid 
```

might give useful information.

---

### Post by btsgreg on 2010-11-03
It/s changed to a RAW file system.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x220fea31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1951422912   975711425    7  HPFS/NTFS
/dev/sda2      1951424512  1953521663     1048576    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2b125f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *      206848   976769023   488281088    6  FAT16

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3de4bf44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76397639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   976768064   488384001    7  HPFS/NTFS

``````
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="W" UUID="2AEC04CFEC04976B" TYPE="ntfs" 
/dev/sdc1: UUID="3A64C55064C51015" TYPE="ntfs" 
/dev/sdd1: LABEL="X" UUID="0650696750695F05" TYPE="ntfs" 
ubuntu@ubuntu:~$
```

---

