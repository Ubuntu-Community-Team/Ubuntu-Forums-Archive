---
title: "Auto e2fsck not enabled?"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by EReckase on 2006-06-06
I've got a HP Pavilion dv8225nr that is happily running Dapper, but after browsing my system log I find the following message:

Jun  6 10:51:27 localhost kernel: [4299060.208000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended

I thought that this should be done automatically at bootup?  This may be related to the fact that this might be coming from an ext3 filesystem on a USB stick, and not an internal drive.

---

### Post by johannes on 2006-06-12
Do you have the disk in /etc/fstab? To make it be automatically checked I think the last number in that row needs to be "1" e.g:
```
# <file system> <dir>           <type>          <options>               <dump>  <pass>
 /dev/hdb1      /media/usb      ext3            defaults                0       1
```

---

### Post by dcstar on 2006-09-29
> **johannes said:**
> Do you have the disk in /etc/fstab? To make it be automatically checked I think the last number in that row needs to be "1" e.g:
```
# <file system> <dir>           <type>          <options>               <dump>  <pass>
 /dev/hdb1      /media/usb      ext3            defaults                0       1
```

"1" is for the root filesystem, it should actually be "2" for the check to happen on non-root filesystems.

In my /etc/fstab, I have the following line which forces a check of my USB stick on boot-up (after the preset count/interval):

```
LABEL=dcstar	/media/dcstar	ext3		rw,noatime,nosuid,nodev			0	2
```
I have labelled my EXT3 drive "dcstar", so it is mounted with that label (handy for mounting specific drives to specific locations).

---

