---
title: "Root doesn't have high enough permission"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by AmandaKerik on 2007-09-15
The latest issue I've had is while I'm root and running nautilus, it STILL won't let me change the permissions on a drive.

Ok, backtracking a bit:
I got a new hard drive a few months ago and I partitioned it using the disk manager in Dapper, but didn't do much more than that (not knowing what, specifically, to do).
I upgraded to Edgy then Feisty - no disk manager, but I did manage to find and understand the chmod, chgrp, etc stuff.
I have 4 partitions on the hard drive - ext3, swap, and 2 vfat (ntfs) partitions. I managed to get the ext3 partition up and running with only a bit of fiddling.
So I tried to apply my knowledge to the ntfs partitions and it's been fighting with me ever since. Refusing to recognise that I'm root, even with sudo - I'm part of the root group, users group and my own group.
One time I got the ext3 one to work, but the other two wouldn't. The next time I got the ntfs ones to work and then was displeased to see the ext3 was back under root-only access. The thing is... once I got ext3 up and working I didn't touch it at all.

At this point I'm tempted to format the whole drive and start over, but knowing how this morning's been going, I won't have high enough access as root, admin and using sudo to do it. :mad:

---

### Post by finer recliner on 2007-09-15
couple questions:

is this hard drive (the one with 4 partitions) the same one that ubuntu is installed?

what is the output of
```

cd /media
ls -al

```

```

cat /etc/fstab

```

```

cat /etc/mtab

```
make sure you do NOT try to edit your mtab file. its for read only purposes.

---

### Post by AmandaKerik on 2007-09-16
>is this hard drive (the one with 4 partitions) the same one that ubuntu is installed?

No, it's a different one, and I have no problems accessing the ext3 partition, just the vfat / ntfs ones. I have the ntfs stuff installed, if you were about to ask.

In the order of request:

```
total 96
drwxr-xr-x 19 root root     4096 2007-09-15 19:46 .
drwxr-xr-x 21 root root     4096 2007-07-11 22:05 ..
lrwxrwxrwx  1 root root        6 2007-01-17 13:10 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-01-17 13:10 cdrom0
-rw-r--r--  1 root root        0 2007-09-15 19:46 .hal-mtab
---xr-x---  1 root root        0 2007-07-11 21:07 .hal-mtab-lock
drwxrwx--- 13 root plugdev  4096 1969-12-31 16:00 hda1
dr-xr-x---  1 root plugdev  8192 2007-07-31 22:35 hda2
drwxr-xr-x  2 root root     4096 2007-07-08 10:25 hdb1
drwxr-xr-x  2 root root     4096 2007-07-08 10:28 hdb2
drwxr-xr-x  2 root root     4096 2007-07-08 10:29 hdb6
drwxrwxr-x  5 root users    4096 2007-09-15 09:21 newubuntudrive
drwxrwxrwx  4 root root    16384 1969-12-31 16:00 ntfs1
drwxrwxrwx  4 root root     8192 1969-12-31 16:00 ntfs2
lrwxrwxrwx  1 root root        4 2007-01-26 15:00 usb -> usb0
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb0
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb1
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb2
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb3
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb4
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb5
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb6
drwxr-xr-x  2 root root     4096 2007-01-26 15:00 usb7

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=ad79726c-7a37-4daf-a05a-e142b476229d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=1147-1C4C /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=D8EC1966EC193FE4 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=d624e0bc-1b52-4eae-baf4-2a11c55e31bb none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# added ext3 partition (hopefully) Sat, 15 Sep
/dev/hdb1       /media/newubuntudrive ext3 defaults 0 0
# added ntfs partition 1
/dev/hdb2       /media/ntfs1 vfat defaults,utf8,umask=000  0 0
# added ntfs partition 2
/dev/hdb6       /media/ntfs2 vfat defaults,utf8,umask=000  0 0
```

Maybe I should change the umask to 007?

```
/dev/hda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-386/volatile tmpfs rw 0 0
/dev/mapper/hda1 /media/hda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/mapper/hda2 /media/hda2 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/newubuntudrive ext3 rw 0 0
/dev/hdb2 /media/ntfs1 vfat rw,utf8,umask=000 0 0
/dev/hdb6 /media/ntfs2 vfat rw,utf8,umask=000 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

I don't even know what mtab does lol...

---

### Post by finer recliner on 2007-09-16
your umask for ntfs1 and ntfs2 are 000 which gives nobody any permissions to access those drives.

try changing the umask for both of those drives in your fstab to 0222. then restart.
take a look here for more info about mounting ntfs: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

