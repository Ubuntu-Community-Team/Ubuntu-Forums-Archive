---
title: "disk mounting issue (question/rant)"
date: 2009-02-05
forum: Hardware
---

### Post by bootdoc on 2009-02-05
why does K/Ubuntu configure the /etc/fstab with an entry for /dev/sdc0 and other such entries for cdrom?   It screws up usb disk recognition i.e. usb disks get mounted as cdrom devices thereby giving bad superblock errors.  It is easily fixed by commenting out the cdrom entries in fstab.

---

### Post by cariboo on 2009-02-05
This is what my cdrom in /etc/fstab looks like:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Check to see what device you cdrom drive is linked to in /dev:

```
ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2009-02-05 08:48 /dev/cdrom -> sr0
ls -l /dev/scd0
lrwxrwxrwx 1 root root 3 2009-02-05 00:48 /dev/scd0 -> sr0
```

Jim

---

