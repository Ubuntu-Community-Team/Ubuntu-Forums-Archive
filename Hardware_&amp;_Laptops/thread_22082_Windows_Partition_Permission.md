---
title: "Windows Partition Permission"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by BigRod on 2005-03-25
I am having problems accessing the files on my Windows paritions.

My setup is like this (results of fdisk -l):
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       37607    18953896+  83  Linux
/dev/hda2           38601      155056    58693477+   7  HPFS/NTFS
/dev/hda3           37608       38600      500472    f  W95 Ext'd (LBA)
/dev/hda5           37608       38600      500440+  82  Linux swap

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hdb2            2551        5005    19719787+   c  W95 FAT32 (LBA)

```

As you can see, I have 2 hard drives.  On the main disk, I have my linux partitions and a 60 gig NTFS partition.  On the secondary drive I have 2 20 gig FAT32 partitions.

I have followed the directions in the [Ubuntu Guide](http://ubuntuguide.org) to a T, and I have had no luck accessing the files on the windows partitions.  When I try to open the NTFS partition, I get an error saying that I do not have permission to access the files.  When I try to open the FAT32 partitions, I can see the files, but nothing is associated properly, directories look the same as files, and nothing will open at all.

For your reference here are the 3 lines I appended to my fstab file:
```
/dev/hda2	/media/windows1	ntfs	umask=0222	0	0
/dev/hdb1	/media/windows2	vfat	umask=000	0	0
/dev/hdb2	/media/windows3	vfat	umask=000	0	0
```

Thanks for your help!

---

### Post by BigRod on 2005-03-25
Oh,

I have also tried doing a chown-ing the mount directories and tried a chmod 755 too, but no luck.

---

### Post by BigRod on 2005-03-25
Bump.  Anybody?

---

### Post by mercurus on 2005-03-26
As far as NTFS goes, PLEASE check that NTFS write support is working properly. I've not looked at it recently, but my understanding has been that NTFS write support is NOT WORKING. Accordingly, there is a good chance that you can break \ wipe \ delete large portions of NTFS partitions using write mode. If that has changed, good :) I'd check it though ... Until then, mount the partition using -o ro

For the vfat partitions, can you write data etc using sudo ?
I'd recommend checking the man page for mount, and appending uid= and gid= options to your vfat mounts so that your normal user and\or group owns the contents of the partition when it is mounted. Otherwise, you won't be able to manipulate it ...

---

### Post by Frayed on 2005-03-26
I'm having the same problem reading a fat partition (permission denied).

/etc/fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /boot           ext2    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda6       /mnt/fat        vfat    defaults,uid=1000,gid=1001,umask=0707  0       0

```

sudo fdisk -l```

Disk /dev/hda: 79.9 GB, 79916820992 bytes
255 heads, 63 sectors/track, 9716 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               8        2550    20426616    7  HPFS/NTFS
/dev/hda2            2551        7785    42050137+   f  W95 Ext'd (LBA)
/dev/hda3            7786        9729    15615180   83  Linux
/dev/hda4   *           1           7       56196   83  Linux
/dev/hda5            2551        3825    10241406    7  HPFS/NTFS
/dev/hda6            3826        7698    31109841    b  W95 FAT32
/dev/hda7            7699        7785      698796   82  Linux swap / Solaris

```

---

### Post by Frayed on 2005-03-26
bah, resolved...changed my umask to 0000....although I'm not so sure this is secure

---

### Post by BigRod on 2005-03-26
[QUOTE=mercurus]As far as NTFS goes, PLEASE check that NTFS write support is working properly. I've not looked at it recently, but my understanding has been that NTFS write support is NOT WORKING. Accordingly, there is a good chance that you can break \ wipe \ delete large portions of NTFS partitions using write mode. If that has changed, good :) I'd check it though ... Until then, mount the partition using -o ro

For the vfat partitions, can you write data etc using sudo ?
I'd recommend checking the man page for mount, and appending uid= and gid= options to your vfat mounts so that your normal user and\or group owns the contents of the partition when it is mounted. Otherwise, you won't be able to manipulate it ...[/QUOTE]

Well, I added auto to the options and for some reason now I can at least see the files on the other partitions, but for some reason on the FAT32 ones I sitll can't see the directories.  I'm guessing my uid is my login and my gid is 600?

What I was planning to do with the NTFS partition is copy everything on it that I need to another drive and then format it in ext3, so I will just change it back to 0222.

---

### Post by mercurus on 2005-03-27
There's another thread just like this one on the boards at the moment, involving an external USB HDD containing an NTFS partition. Have a look at that one.

uid is 1000 for the first user, and gid is usually 1000 too.

---

### Post by BigRod on 2005-03-28
Thanks, I just decided I would pull everything I needed off of the NTFS partition onto my ext3 partition and reformat the NTFS to ext3.  I did the same with part of the other drive, but then I figured out how to setup the FAT32 permissions properly, so all is well.

---

### Post by mercurus on 2005-03-28
If it is any help, there are windows applications that can safely read ext2 and ext3 partitions (if you still require windows interoperability)

Cheers
mercurus

---

### Post by BigRod on 2005-03-29
Nope, I went all the way and completely got rid of Windows, hopefully for the last time.  The only reason I can see that I would ever need it again is if I got back into gaming and couldn't get a game I wanted running in Linux.

---

