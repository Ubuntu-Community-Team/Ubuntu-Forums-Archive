---
title: "Computer crash, cant write to hard drives"
date: 2009-03-23
forum: Hardware
---

### Post by houseonfire on 2009-03-23
My computer crashed because of a video card driver that is half unsupported by ubuntu. But now I cannot access my external, and internal secondary drives.


tim@tim-desktop:~$ sudo fdisk -l /media/sdb1/
[sudo] password for tim: 
Warning: Unable to open /media/sdb1 read-write (Is a directory).  /media/sdb1
has been opened read-only.
Warning: Unable to open /media/sdb1 read-write (Is a directory).  /media/sdb1
has been opened read-only.
Error: /media/sdb1: unrecognised disk label          

Not sure really how to repair this.. Without formatting... Which is very very close to not an option.

---

### Post by aurelieng on 2009-03-23
Fdisk should be called on the block device (i.e. /dev/sdb1), not on the mount point itself. You can try ```
sudo fdisk -l /dev/sdb1
```
Then, try to mount it ```
sudo mount /dev/sdb1 /media/sdb1
```
If it does not work, you should check it for errors using fsck.ext3:
```
sudo fsck.ext3 /dev/sdb1
```

Then try to mount it again.

---

### Post by houseonfire on 2009-03-23
Thanks for the tip. It worked.
I'll be sure to save that for later.

---

