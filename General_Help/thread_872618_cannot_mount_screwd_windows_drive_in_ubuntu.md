---
title: "cannot mount screwd windows drive in ubuntu"
date: 2008-07-28
forum: General Help
---

### Post by braddarb12345 on 2008-07-28
Ive got a dell inspiron 6400 and it was running windows xp home service pack 2 also running now latest version of the live ubuntu 8 not installed but the first option try without installing when u boot the cd

Ive found other threads about this but have got lost in what they were talking about also i ran a few other commands which might help aswell so you wont have to ask maybe.... please help me get my data back

getting a message of

```
ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk
root@ubuntu:~# mount -t ntfs-3g /dev/sda2 /media/disk -o force
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```


also

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       14017   112551390    7  HPFS/NTFS
/dev/sda3           14018       14409     3148740   db  CP/M / CTOS / ...

```


anyone help? thanks :)

---

### Post by lisati on 2008-07-28
Please be patient: There are a couple of replies in your other thread about this problem: see [http://ubuntuforums.org/showthread.php?t=872609](http://ubuntuforums.org/showthread.php?t=872609)

---

### Post by dmizer on 2008-07-28
Thread closed.  Please do not create duplicate threads, it just creates problems for those of us attempting to help you.

---

