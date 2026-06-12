---
title: "USB Flash Drive"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by 111787 on 2006-02-09
It did work but now:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Error: could not execute pmount 

dmesg | tail yields:
> [4295077.796000] VFS: Can't find ext3 filesystem on dev sda.
[4295077.807000] VFS: Can't find ext3 filesystem on dev sda.
[4295077.818000] VFS: Can't find an ext2 filesystem on dev sda.
[4295077.829000] VFS: Can't find an ext2 filesystem on dev sda.
[4295077.848000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4295077.868000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4295077.883000] XFS: bad magic number
[4295077.883000] XFS: SB validate failed
[4295077.897000] XFS: bad magic number
[4295077.897000] XFS: SB validate failed 

---

### Post by Teroedni on 2006-02-09
Have you formatted it:O?

You should not format a flash disk

---

### Post by 111787 on 2006-02-09
I didn't format it.  I don't think i even added or removed any files between the time i removed it to the time i tried to mount it again.

---

### Post by K.Mandla on 2006-02-10
I had a similar problem with a CF card reader that wouldn't mount properly. I was getting an error like that when I gave it *sudo mount -t vfat /dev/sda /media/cfreader*. (Of course, I had created the /media/cfreader folder before that.)

I double-checked the drive assignment with *sudo fdisk -l*, then gave it this command. ...

```
sudo mount -t vfat /dev/sda1 /media/cfreader
```
It seemed to work O.K. after that. The problem was, I was using */dev/sda* in my command, but the reader was assigned */dev/sda1*. I don't know if perhaps you've made the same mistake, but I hope this helps.

---

