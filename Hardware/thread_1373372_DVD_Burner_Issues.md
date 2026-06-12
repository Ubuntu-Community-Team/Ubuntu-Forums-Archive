---
title: "DVD Burner Issues"
date: 2010-01-05
forum: Hardware
---

### Post by linarau on 2010-01-05
Hey everyone.  I recently installed Ubuntu 9.10 on an extra box my parents had lying around.  It has a CD-ROM and DVD burner installed.  There is no problem with the CD drive, but I cannot get the DVD burner working.  Ubuntu acknowledges that it exists and it shows up as "Drive".

When I click on "Drive" I get the following error:
"Unable to scan  Drive for media changes"
"Device is not active"

I've searched the forums, but have not been able to find anyone with the same exact problem (I apologize if I've missed a thread).  I've been using Ubuntu for some time now, but I still consider myself a noob.  My Fstab is pretty cluttered, but here are the contents:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7c2b3265-0190-4c60-959b-b65c900c24bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0ab51909-7763-47ef-9f4b-2ce74901bad8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any help would be greatly appreciated.

---

