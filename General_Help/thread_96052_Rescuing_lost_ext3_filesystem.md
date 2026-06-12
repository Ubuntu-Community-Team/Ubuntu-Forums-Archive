---
title: "Rescuing lost ext3 filesystem?"
date: 2005-11-28
forum: General Help
---

### Post by Morrigu on 2005-11-28
Seems like I made a bit of a mistake while partitioning my hd. I made W95 Extended and mkfs.ext3 to this disk. It worked fine and I copied data to it.

After boot mount won't recognize the filesystem. I reconfigured it to W95 Extended + Linux logical, but now I need to tell Ubuntu that hdd5 (linux logical) is ext3, without deleting the data on this disk. 

Is this possible?

---

### Post by amohanty on 2005-11-28
can you post the contents of your fstab

in a terminal (Applications->Accessories->Terminal) type:
cat /etc/fstab

and post the result

AM

---

### Post by Morrigu on 2005-11-28
**fstab**
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               reiserfs notail          0       1
/dev/hda5       /media/FLEVY    ext3    defaults 0      0
/dev/hdb5       /media/DLEVY    ext3    defaults 0      0
#/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0   0
#/dev/hdb1      /media/levy1    ntfs    nls=utf8,umask=0222 0   0
#/dev/hdd1      /media/ELEVY    ext3    nls=utf8,umask=0222 0   0

```

The problem disk is hdd. Yes, currenty it's commented out.

**/dev**
```

lindmmik@ip-81-175-140-175:~$ ls /dev/hdd*
/dev/hdd  /dev/hdd1  /dev/hdd5

```

**fdisk -l**
```

lindmmik@ip-81-175-140-175:~$ sudo fdisk -l /dev/hdd
Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321    f  W95 Ext'd (LBA)
/dev/hdd5               1       19457   156288289+  83  Linux

```

Notice that I just created hdd5 with fdisk, after boot I could just see W95Ext. So now I need to tell linux that hdd5 is ext3, and somehow rescue the data from there..

**mount**
```

lindmmik@ip-81-175-140-175:~$ sudo mount -t ext3 /dev/hdd5 /media/ELEVY
mount: wrong fs type, bad option, bad superblock on /dev/hdd5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

**syslog**
```

Nov 28 11:53:27 localhost kernel: [4311423.481000] VFS: Can't find ext3 filesystem on dev hdd5.

```

---

### Post by amohanty on 2005-11-28
can you try mounting it as vfat:
mount -t vfat /dev/hdd5 /media/ELEVY

AM

---

### Post by Morrigu on 2005-11-30
**mount -t vfat**
```

lindmmik@ip-81-175-140-175:~$ sudo mount -t vfat /dev/hdd5 /media/ELEVY
mount: wrong fs type, bad option, bad superblock on /dev/hdd5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

