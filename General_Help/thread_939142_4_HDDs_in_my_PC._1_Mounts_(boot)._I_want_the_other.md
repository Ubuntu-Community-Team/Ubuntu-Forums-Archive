---
title: "4 HDDs in my PC. 1 Mounts (boot). I want the others to mount."
date: 2008-10-05
forum: General Help
---

### Post by Roasted on 2008-10-05
I have 4 drives in my computer, which are used as network shares via samba for other users to write data to. The main one I use mounts, obviously, as I boot into Ubuntu. But the other 3 do not.

What can I do?
FSTAB
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2ec37113-822b-4a5e-b87f-befc12f2ea62 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=cc395d41-d5db-4534-9c90-98a2edca20bd /home           ext3    relatime        0       2
# /dev/sda2
UUID=0c602899-a3f4-4676-b46f-62e12005db60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```



FDISK -L
```

jason@jason-hardy:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007269c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16771676

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        5223      996030   82  Linux swap / Solaris
/dev/sdb3            5224        7168    15623212+  83  Linux
/dev/sdb4            7169       60801   430807072+  83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux
jason@jason-hardy:~$ 


```

---

### Post by Elfy on 2008-10-05
Add them to fstab and all shoould be well, the syntax/options for mounting the ntfs is in bodhis fstab thread which is worth the read.

[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

[http://ubuntuforums.org/showthread.php?t=28313](http://ubuntuforums.org/showthread.php?t=28313)

---

### Post by porchrat on 2008-10-05
As mentioned above...modify /etc/fstab and add the drives there.  To find their UUID numbers use this command:

```
sudo blkid
```

---

### Post by Roasted on 2008-10-05
Okay, here's my update /etc/fstab. It seems to be working since I logged out/back in and they auto mounted. But I have another question. See below.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2ec37113-822b-4a5e-b87f-befc12f2ea62 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=cc395d41-d5db-4534-9c90-98a2edca20bd /home           ext3    relatime        0       2
# /dev/sda2
UUID=0c602899-a3f4-4676-b46f-62e12005db60 none            swap    sw              0       0

# /dev/sda1 - LOCALBACKUP
/dev/sda1 UUID=c5bd948f-dbe5-4d09-8aaf-185b4fdb56a7 /media/localbackup	ext3 
# /dev/sdc1 - STORAGE
/dev/sdc1 UUID=5d23ae76-162d-451a-bf27-fdd8fadf6f22 /media/storage	ext3
# /dev/sdd1 - STORAGEBACKUP
/dev/sdd1 UUID=772764b7-e571-4897-ba6d-ded412a5e814 /media/storagebackup	ext3


/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```


Here's my fdisk -l
```

jason@jason-hardy:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007269c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16771676

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        5223      996030   82  Linux swap / Solaris
/dev/sdb3            5224        7168    15623212+  83  Linux
/dev/sdb4            7169       60801   430807072+  83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux
jason@jason-hardy:~$ 


```


Check out my /etc/fstab. Notice sda 2, 3, 4? Where in the world is sda2, sda3, sda4 coming from? My drive "sda" is a blank hard drive with 1 partition (EXT3) spanning across the entire drive. How does fstab have inputs from partition 2 3 and 4? I didn't put those in. That's how it happened on its own.

---

### Post by Roasted on 2008-10-05
Aight. That didn't really work. When I booted up, my drives weren't visible... however I have a mount script to mount the drives to their designated locations, so I ran that script and suddenly everything came up and worked. BUT, they didn't auto mount.

I ended up switching my fstab back to the original.

Any ideas what went wrong? My updated fstab (the one that didn't work) is above.

---

### Post by Mister.Vash on 2008-10-05
The fstab file you posted has some errors in it

This is correct
```

# /dev/sda4
UUID=cc395d41-d5db-4534-9c90-98a2edca20bd /home           ext3    

```

This is not
```

# /dev/sda1 - LOCALBACKUP
/dev/sda1 UUID=c5bd948f-dbe5-4d09-8aaf-185b4fdb56a7 /media/localbackup	ext3 

```

Basically the UUID is the disk and /dev/sda1 is also a disk - so your are including two drive on a single mount line.  To fix this, get rid of /dev/sda1 - the following should be correct.
```

# /dev/sda1 - LOCALBACKUP
UUID=c5bd948f-dbe5-4d09-8aaf-185b4fdb56a7 /media/localbackup	ext3 

```

The line with a hash in front is a comment line - it's there for your reference. On the next line down the
UUID=    That is the drive your are trying to mount
/media/localbackup   is the mount point
ext3     is the file system


So for all the lines that have a /dev device in from of a UUID, remove the /dev device so it start of with a UUID.  Reboot and lets see what happens now.

---

