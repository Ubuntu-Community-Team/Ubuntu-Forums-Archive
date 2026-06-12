---
title: "cannot format usb drive"
date: 2010-04-30
forum: Hardware
---

### Post by albertkao on 2010-04-30
Suddenly my 4GB usb thumb drive cannot be formatted by Ubuntu or Windows.
My usb drive does not have any switch on it to make it readonly.
```
$ sudo mkfs.ext3 -F  /dev/sdg1
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdg1: Read-only file system while setting up superblock
```

---

### Post by wilee-nilee on 2010-04-30
Have you tried gparted in Ubuntu in system-admin-gparted.

Or right clicking on the icon of the thumb and then format.

---

