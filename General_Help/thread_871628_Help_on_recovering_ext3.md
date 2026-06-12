---
title: "Help on recovering ext3"
date: 2008-07-27
forum: General Help
---

### Post by dannybuntu on 2008-07-27
Hi, I need help on mounting and possibly recovering my ext3 partition. This partition used to be a FAT32 partition on a second device. I formatted it and changed it into an ext3 partition as a secondary backup. I reinstalled xubuntu on the first devices primary partition. But then I wasn't able to mount it during the installation since it would be formatted if I did.

So I installed xubuntu without mounting the partition during installation. 

After installation I tried:

```
sudo mount -t ext3 /dev/sdb5 /media/hdb
```

It said:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Then:

```
dmesg | tail
```

Then: 

```
[15289.498440] sd 3:0:0:0: [sdd] Write Protect is off
[15289.498466] sd 3:0:0:0: [sdd] Mode Sense: 03 00 00 00
[15289.498476] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[15289.500442]  sdd: sdd1
[15289.513837] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[15289.518823] sd 3:0:0:0: Attached scsi generic sg3 type 0
[15308.642628] kjournald starting.  Commit interval 5 seconds
[15308.652721] EXT3 FS on sdd1, internal journal
[15308.653225] EXT3-fs: mounted filesystem with ordered data mode.
[24185.722278] VFS: Can't find ext3 filesystem on dev sdb5.
```

What should I do next?

---

### Post by dexter.deepak on 2008-07-27
are you trying the right partition ?
post the output of
```
sudo fdisk -l
```

...and i hope you formatted the disk to ext3 "properly".

---

### Post by dannybuntu on 2008-07-27
Thanks deepak for the quick reply. I formatted it using debian's partitioner during installing of debian.

So a brief timeline:

1. I installed debian etch
   - I formatted FAT32 to ext3 using debian install partitioner 
2. I put some files in said partition
3. I remove debian
4. I install xubuntu but did not mount during install since it automatically checks the format tick box 
5. I tried the commands above

Here you go:

```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26ae83cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1147     9213246    7  HPFS/NTFS
/dev/sda2            1148        4794    29294527+  83  Linux
/dev/sda3            4795        4998     1638630   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a179a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2423    19462716    7  HPFS/NTFS
/dev/sdb2            2424        4865    19615365    5  Extended
/dev/sdb5            2424        4865    19615333+  83  Linux

Disk /dev/sdd: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d75c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          62      497983+  83  Linux
```

---

### Post by geirha on 2008-07-27
What happens if you have mount autodetect the filesystem. Maybe it's ext2 or reiserfs?
```
sudo mount /dev/sdb5 /media/hdb
```

---

### Post by dannybuntu on 2008-07-27
It is ext3. 

```
mount: you must specify the filesystem type
```

---

### Post by geirha on 2008-07-27
Obviously something wrong with the filesystem then. What does fsck say?
```
sudo fsck /dev/sdb5
```

---

### Post by dannybuntu on 2008-07-27
```
fsck 1.40.11 (17-June-2008)
e2fsck 1.40.11 (17-June-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

---

### Post by geirha on 2008-07-27
Hm, it sounds like that partition is simply empty. No filesystem on it ...

See if [testdisk](http://www.cgsecurity.org/wiki/TestDisk) can recover anything. You'll find it as [testdisk](apt:testdisk) in the repositories.

---

### Post by dexter.deepak on 2008-07-27
did you try e2fsck as suggested in the output of fsck ??

---

### Post by dannybuntu on 2008-07-27
Strange, this is the output:

```
e2fsck 1.40.11 (17-June-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb5
Filesystem mounted or opened exclusively by another program?

```

@geirha

Oh no, I was afraid you would say that. I already tried testdisk and "analyze" does not show the filesystem at all. 

Even photorec does not show anything. Oh no.

---

### Post by vanadium on 2008-07-27
It looks like the partition was not properly formatted. Since there is no data there, I would first attempt to reformat it:

```

sudo umount /dev/sdb5
sudo mkfs -t ext3 /dev/sdb5

```

(First command should give you an error if indeed the partition is not mounted in the first place).

This should give you a freshly ext3 formatted partition.

Test mounting first:
```

sudo mkdir temp
sudo mount /dev/sda5 temp
sudo touch temp/this-is_just_to_test
ls temp
sudo rm temp/this-is_just_to_test
sudo umount /dev/sda5

```

If all works well 9no error messages, "ls temp" shows you the dummy file this-is_just_to_test that you created on the volume, etc., then you can mount it automatically during startup by including the drive in /etc/fstab. Post back if you need help with the latter.

---

### Post by geirha on 2008-07-27
> **dannybuntu said:**
> Strange, this is the output:

```
e2fsck 1.40.11 (17-June-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb5
Filesystem mounted or opened exclusively by another program?

```

@geirha

Oh no, I was afraid you would say that. I already tried testdisk and "analyze" does not show the filesystem at all. 

Even photorec does not show anything. Oh no.

sda and sdb seem to be almost the same size. Could it be you've repartitioned the wrong disk?

---

### Post by dannybuntu on 2008-07-27
> **vanadium said:**
> It looks like the partition was not properly formatted. Since there is no data there, I would first attempt to reformat it:

```

sudo umount /dev/sdb5
sudo mkfs -t ext3 /dev/sdb5

```

(First command should give you an error if indeed the partition is not mounted in the first place).

This should give you a freshly ext3 formatted partition.

Test mounting first:
```

sudo mkdir temp
sudo mount /dev/sda5 temp
sudo touch temp/this-is_just_to_test
ls temp
sudo rm temp/this-is_just_to_test
sudo umount /dev/sda5

```

If all works well 9no error messages, "ls temp" shows you the dummy file this-is_just_to_test that you created on the volume, etc., then you can mount it automatically during startup by including the drive in /etc/fstab. Post back if you need help with the latter.

Good morning all! at least here.

I think I am missing something here. I put data on sdb5 when I was using debian etch. I accessed the files when I was using debian etch. If the information shows that there are no files then I am royally screwed. 

A question though - if I format it (again) - I am pretty sure that there would be no files in the partition no?

@geirha

sda has 3 partitions
NTFS - where I am posting now - winxp
EXT3 - where I installed xubuntu
swap

sdb has 2 partitions (or 3 if I am wrong)
sdb1 - NTFS - some win files
sdb2/5 - unpartitioned which was supposed to be the ext3 backup partition

---

### Post by dannybuntu on 2008-07-28
Guys, I reformatted it using gparted as FAT32 instead of ext3 as suggested by vanadium since I wanted to see those files on windows too. 

Now look at this: 

[http://i106.photobucket.com/albums/m271/dan_rgarcia/gparted.jpg](http://i106.photobucket.com/albums/m271/dan_rgarcia/gparted.jpg)

It shows there that it is using 9 GB of it - but when viewing it in thunar or cli it shows no file? 

even ls -a does not show hidden folders.

Strange aint it?

---

### Post by caljohnsmith on 2008-07-28
Actually, it says 9.41 MiB, not GiB. :) I'm not sure if that is normal for a FAT partition or not to have that used by default, but 9 MB is certainly nothing to worry about.

---

### Post by vanadium on 2008-07-28
```
I reformatted it using gparted as FAT32 instead of ext3 as suggested by vanadium 
```

?? I did not advise that? In a case of dual-boot, I'd advise ntfs or even staying with ext3 and using the ext driver in Windows. fat32 is in my opinion usefull only if you need maximum compatibility, for example if you need to carry the drive around and connect it to computers elsewhere.

Probably indeed, your 9 Mb is "file system overhead".

---

### Post by dannybuntu on 2008-07-29
Aye. Thanks for pointing that out cal. Anyway, what I did was just forgot the whole thing and got a spare drive where the original data comes from. Lesson learned 1 backup is not enough. Thanks to all who helped. This is a lesson I just have to learn and relearn again and again. 1 backup is not enough. 1 backup is not enough.1 backup is not enough. 1 backup is not enough.1 backup is not enough. 1 backup is not enough.1 backup is not enough. 1 backup is not enough.1 backup is not enough. 1 backup is not enough.1 backup is not enough. 1 backup is not enough.

---

