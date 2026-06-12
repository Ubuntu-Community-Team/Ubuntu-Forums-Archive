---
title: "SDHC is read-only for some reason (yes the switch is on read)"
date: 2009-04-26
forum: Hardware
---

### Post by nhat on 2009-04-26
(yes the switch is on read\write)

I have a dell mini 9 and I recently upgraded to 9.04. At first the SDHC was working well than when I booted up my mini just recently, I noticed my disk-1 folder have a lock on it.

I'm logged in as root and when I changed my permission, I get an error message: The permission could not be changed. Sorry, could not change the permissions of the "disk-1": Error setting permissions: read-only file disk.

I used mount -remount,rw /media/hda1 and fsck but nothing work. So I put the SDHC in my vista machine and it reads and writes like a charm.

So far my experience with Ubuntu have been bumpy, always things pop up like this make menial task a chore. I hope someone can help with my issue. Thanks.

---

### Post by binukavumkal on 2009-04-26
Hi,

It seems this is similar to the issue

[http://ubuntuforums.org/showthread.php?t=1136523](http://ubuntuforums.org/showthread.php?t=1136523)

and is resolved


Thanks

---

### Post by nhat on 2009-04-26
Thanks for the reply. I used the command in that post and got this:

root@buntu-laptop:~# sudo dosfsck -a /media/disk-1
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
open /media/disk-1:Is a directory

Still didn't work. When I had 8.04, the SDHC worked.

I used the command dmesg and got this:
 224.259703] FAT: Filesystem panic (dev mmcblk0)
[  224.259722]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  313.751497] nautilus[3843] general protection ip:b7a582f8 sp:bf9d0950 error:0 in libgobject-2.0.so.0.2000.1[b7a2f000+3c000]
[  327.913057] FAT: Filesystem panic (dev mmcblk0)
[  327.913071]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  582.937462] FAT: Filesystem panic (dev mmcblk0)

---

### Post by doogy2004 on 2009-04-26
try the following command it will give you a list of mounted disks and their usage.

```
df -h
```

This is one way to determine if the disk is actually mounted on the folder.

---

### Post by nhat on 2009-04-26
Ok I did a chkdsk in windows and it fixed the problem. I tried doing the dosfsck but I get that message...

---

