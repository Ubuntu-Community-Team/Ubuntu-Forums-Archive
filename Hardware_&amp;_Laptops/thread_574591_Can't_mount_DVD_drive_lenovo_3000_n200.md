---
title: "Can't mount DVD drive lenovo 3000 n200"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by piege on 2007-10-13
Hi, 

I can't mount my cd drive i get an error saying' mount: special device /dev/hdb does not exist'.

I tried to figure out how to solve the problem but I'm a bit confused and I would appreciate a little help please 

 Apparently this file might help explain the problem 

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=30aa2df6-4b55-40b2-a67e-3300c69fac13 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=081d101d-7786-4d12-a1c1-5d10daf35639 /home           ext3    defaults        0       2
# /dev/sda5
UUID=6acf1a34-23ab-499d-8c82-6d2bd5f52391 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by akiragtr on 2008-06-24
Hi! I have the same notebook and had the same problem. Try using acpi=off as a kernel boot parameter. It works for me.

[https://bugs.launchpad.net/ubuntu/+bug/67670/comments/3](https://bugs.launchpad.net/ubuntu/+bug/67670/comments/3)

---

