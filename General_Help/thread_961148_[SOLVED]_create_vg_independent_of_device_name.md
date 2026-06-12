---
title: "[SOLVED] create vg independent of device name"
date: 2008-10-28
forum: General Help
---

### Post by srimalik on 2008-10-28
Hi, All

I have an external disk on of the partitions is under LVM control and there is a single LV on it.

The disk is a pluggable USB drive. 

There is no problem when only this disk is connected to the computer or this is the first external disk. It is recognized as /dev/sdb and the PV is on /dev/sdb8.

But when this disk is connected when another external disk is already connected to the system it is recognized as /dev/sdc and I am not able to use the partition under LVM control. mount fails as the vg is mapped with /dev/sdb8 and not sdc8

How can I create a transparent PV i.e independent of device names.
I am presently investigating on disk UUIDs,  but this will be my first encounter with UUIDs and I hope I am on the right track.


Thanks
-Sri

---

### Post by dcstar on 2008-10-28
> **srimalik said:**
> 
.........
How can I create a transparent PV i.e independent of device names.
I am presently investigating on disk UUIDs,  but this will be my first encounter with UUIDs and I hope I am on the right track.


Use Disk Labels.

---

### Post by srimalik on 2008-10-28
Thanks David

It seems UUID are related to file system and not with partitions or LVs :(
I will investigate disk labels  and update . 

-Sri

---

### Post by jerome1232 on 2008-10-28
UUID's should work just fine, as will labels.

---

### Post by srimalik on 2008-10-28
The problem is that I could not find the UUID of the LV.
BTW, I have written two small scripts which will take care of the problem

Here are those:
$ cat activate-external-disk.sh 
#!/bin/sh
vgimport vgdisk
vgchange -a y /dev/vgdisk
mount /dev/vgdisk/lvol0 /mnt/usb
[krishan@l3-lr893 programs]$ cat remove-external-disk.sh 
#!/bin/sh
sync
umount /dev/vgdisk/lvol0
vgchange -a n /dev/vgdisk
vgexport vgdisk
[krishan@l3-lr893 programs]$

---

### Post by jerome1232 on 2008-10-28
will show logical volumes uuid's
```
lvdisplay
```

---

### Post by srimalik on 2008-10-29
I think using UUID will not solve the issue, I have to anyway stop and export the volume group before I remove the disk. Else, there is not way for LVM to know about the change.

---

