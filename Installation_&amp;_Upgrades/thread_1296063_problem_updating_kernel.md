---
title: "problem updating kernel"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by iswan on 2009-10-20
I found this problem when trying out mkinitrd

root@arnanda-laptop:/boot# mkinitrd -o initrd.img-2.6.31.2 2.6.31.2
/usr/sbin/mkinitrd: add_modules_dep_2_5: modprobe failed
FATAL: Module sg not found.
FATAL: Module sd_mod not found.
WARNING: This failure MAY indicate that your kernel will not boot!
but it can also be triggered by needed modules being compiled into
the kernel.


need help.

---

