---
title: "[SOLVED] Possible data loss"
date: 2008-09-11
forum: General Help
---

### Post by wiseguyxp on 2008-09-11
I have 2 hard drives in my computer.  The first (80gb) had xp pro on it.  The second (320gb) had my backup data and music, setup files for applications, and lots of documents for school that I don't want to lose.  My windows started messing up (not surprising), and I was going to reinstall until I remembered that I had an image backup of my 80gb drive on the 320gb drive.  

So, I booted up into Ghost for Linux (g4l) and used it to restore my old image back to my hard drive.  Everything went okay.  I booted up into Windows and tried to access the 320gb drive, but it didn't work.  I installed Ext2IFS (I guess I didn't include it in the image) and tried to access the drive, but it now said it was NTFS!  I wondered if this was an error from the reimaging, but I reinstalled XP with the CD and it still did the same thing.  When I double click the drive in my computer, it asks me if I want to format it.

I booted into Ubuntu 8.04 Live and checked the drive.  It comes up with the correct drive label (data) and it says it's Ext3 when I look in the drive properties.  I try to look at the drive while it's mounted, but nothing is inside the mount location.  In the drive properties, it also shows that the drive has 190GB used already.  I know the data is still there, but is there any way that I can recover it?  What could've gone wrong?

I could survive without it, but there's a lot that I would need to do to get anywhere close to where it was before.  Please help.

---

### Post by aysiu on 2008-09-11
When you have the live CD booted up, can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
sudo fdisk -l
df -h
```

---

### Post by wiseguyxp on 2008-09-11
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace72c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0501d572

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
```

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G   16M  1.5G   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 1.5G   16M  1.5G   2% /lib/modules/2.6.24-16-generic/volatile
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   44K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
tmpfs                 1.5G   16K  1.5G   1% /tmp
gvfs-fuse-daemon      1.5G  122M  1.4G   9% /home/ubuntu/.gvfs
```

---

### Post by aysiu on 2008-09-11
Well, the 300 GB drive looks NTFS to me.

Let's see if we can't mount it. ```
sudo mkdir /recovery
sudo mount -t ntfs /dev/sdb1 /recovery -o nls=utf8,umask=0222
ls /recovery
```

---

### Post by wiseguyxp on 2008-09-11
```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /recovery -o nls=utf8,umask=0222
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by aysiu on 2008-09-11
Hm. Maybe the partition table is damaged.

Can someone else weigh in on this?

---

### Post by wiseguyxp on 2008-09-11
Could I use the Ultimate Boot CD to repair the partition table?

---

### Post by wiseguyxp on 2008-09-12
Well, I booted into the Ultimate Boot CD, then used TestDisk and wrote over my partition table with Linux being the filesystem.  Everything is now working as it used to.

---

