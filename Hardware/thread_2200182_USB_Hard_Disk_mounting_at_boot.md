---
title: "USB Hard Disk mounting at boot"
date: 2014-01-17
forum: Hardware
---

### Post by z7APXKm on 2014-01-17
I have a matching pair of WD 500GB USB hard disks that I'm using as rotating backup.

The problem is that I can't get them to mount automatically at boot.

In my fstab I've got the following:
```
# external backup disk
UUID=a5b5a24a-4c81-4ffa-941e-07cdb18b5bda       /mnt/backup     ext3    defaults,nobootwait     0       0
UUID=b6c069f0-8c41-491e-85aa-aba3773d1bca       /mnt/backup     ext3    defaults,nobootwait     0       0
```

Obviously only one of these is going to be connected at any one time, so one of them will be wrong.

If I remove the nobootwait, the whole system hangs at startup.

If I manually mount the disk by typing ```
mount /dev/sdf1
``` or ```
mount /dev/sda1
``` (it tends to switch) after bootup all seems OK.

---

### Post by z7APXKm on 2014-02-01
Any ideas?  Mounting manually is a bit tedious.

---

