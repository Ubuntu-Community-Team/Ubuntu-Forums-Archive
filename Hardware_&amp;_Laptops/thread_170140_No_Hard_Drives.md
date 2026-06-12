---
title: "No Hard Drives"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by pkbarber on 2006-05-04
I just tried to mount an NTFS disk using: [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

I cant access any of my drives.  However, I didnt even think to look at them after the install.  I just jumped into getting this box up and running how I wanted it.  There was no information on the master drive to begin with.  In the File System menu my drives are red boxes with Xs through them.
This is the out put of my l -ls media command
```
ls -l /media
total 8
lrwxrwxrwx  1 root root    6 2006-04-25 17:15 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-04-25 17:15 cdrom0
lrwxrwxrwx  1 root root    7 2006-04-25 17:15 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2006-04-25 17:15 flopp
```

---

### Post by nanotube on 2006-05-04
post your output of command "df", "cat /etc/fstab" and "sudo fdisk -l" and we will try to figure out what's up :)

---

### Post by aysiu on 2006-05-04
[QUOTE=pkbarber]I just tried to mount an NTFS disk using: [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)[/QUOTE] Did you read the red type in the beginning? > Warning! Ntfs writing support is still experimental! You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk!

If you like your data, you should mount NTFS as read-only.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by pkbarber on 2006-05-04
I read the warning but have nothing to lose, just trying to learn a lil something new.

```

df
/dev/hda1              9408480   2344040   6586508  27% /
tmpfs                   160900         0    160900   0% /dev/shm
tmpfs                   160900     12588    148312   8% /lib/modules/2.6.12-10-386/volatile


```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```

sudo fdisk -l
Disk /dev/hda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1245      441787+   5  Extended
/dev/hda5            1191        1245      441756   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS
```

THX

---

### Post by nanotube on 2006-05-04
well, it looks like your linux partition is mounted properly... now to mount your ntfs readonly, add this line to the end of your fstab:
```
/dev/hdc1       /mnt/win        ntfs    ro,nls=utf8,uid=1000,umask=0277 0       0
```
and then run commands:
```
sudo mkdir -p /mnt/win
mount /mnt/win
```
and your ntfs will be mounted with permissions for your username. (for detailed explanation of what all the options mean, click the first link in my sig, and go to the "fstab" section).

now, to mount ntfs read+write, just change the umask to 0077, and remove the "ro," option.

but if you do write/change files on the ntfs partition, you want to install ntfsprogs with
```
sudo apt-get install ntfsprogs
```
that contains a tool called "ntfsfix" which you should use to fix the ntfs partition - otherwise if you try to boot windows after writing, it will be severely borked.

well... have fun.

---

### Post by nanotube on 2006-05-04
well, it looks like your linux partition is mounted properly... now to mount your ntfs readonly, add this line to the end of your fstab:
```
/dev/hdc1       /mnt/win        ntfs    ro,nls=utf8,uid=1000,umask=0277 0       0
```
and then run commands:
```
sudo mkdir -p /mnt/win
mount /mnt/win
```
and your ntfs will be mounted with permissions for your username. (for detailed explanation of what all the options mean, click the first link in my sig, and go to the "fstab" section).

now, to mount ntfs read+write, just change the umask to 0077, and remove the "ro," option.

but if you do write/change files on the ntfs partition, you want to install ntfsprogs with
```
sudo apt-get install ntfsprogs
```
that contains a tool called "ntfsfix" which you should use to fix the ntfs partition - otherwise if you try to boot windows after writing, it will be severely borked.

well... have fun.

---

