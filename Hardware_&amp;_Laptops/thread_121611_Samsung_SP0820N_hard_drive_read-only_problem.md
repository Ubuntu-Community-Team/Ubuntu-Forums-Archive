---
title: "Samsung SP0820N hard drive read-only problem"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by rantak on 2006-01-25
I've installed ubuntu along my Windows XP about a month ago and everything has been working alright
but suddenly one of my harddrives gives me problems. This harddrive has three partitions

/dev/hdb1 (vfat) Shared with windowsXP
/dev/hdb2 (ext3) Main linux partition
/dev/hdb5 Swap partition

When I boot into linux the harddrive is working correctly (all partitions), but after a while the /dev/hdb1 partition turns into read-only mode. For example if I try to delete something it gives the following error.
rm: cannot remove `xyz': Read-only file system
(Sudo doesn't help.)
The weird thing is that everything works correctly for 30 mins - few hours until this error occurs. The main partition /dev/hdb2 works correctly all the time.

Here's my fstab file
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1 	/media/Matrox 	ntfs umask=0222 0 0
/dev/hdb1 	/media/Sammy 	vfat umask=000	0 0
/dev/sdb1	/media/ipod	vfat	sync,user,noauto,umask=000	0 0

---

### Post by nihilocrat on 2006-01-25
for a quick fix, try unmounting and remounting the drive.
```

sudo umount /media/Sammy
sudo mount /media/Sammy

```

Oh, and you might want to change the umask for Sammy. Right now it's 000, so either remove the umask argument or set it to something nicer like 664. That shouldn't really be a source of problems, because it would give a "permission denied" error instead of a "read-only filesystem".

Adding the "defaults" argument might be a good idea too.

The most confusing part of this problem, and which I don't really know what to do about, is the fact that it suddenly does it after awhile :-P

---

