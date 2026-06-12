---
title: "/dev/fd0 is not a valid block device"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by lptr on 2007-11-08
Gutsy does not like to address fd0. Inbetween I changed drive to be safe that there is no HW problem. I formated on another system a new floppy. After inserting and trying to open Drive A from inside vmware/wksta XP installation LED is changing state to on that's it.

dmesg tells me there is fd0 found
# lsmod | grep floppy
floppy                 60004  0

manually mounting:
# mount -t vfat /dev/fd0 /mnt
mount: /dev/fd0 is not a valid block device

any ideas? a problem with vmware?

rob*

---

