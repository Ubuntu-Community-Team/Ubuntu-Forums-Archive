---
title: "cdrom behavior"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by kbee on 2008-02-29
Hi there,

I'm new to unix, running xubuntu 7.04. I have an AOPEN CD-RW CRW5224. When I boot without a cd preloaded, I have to "mount /dev/cdrom" before I can open the drawer to load a cd; no cd icon appears on the desktop, but I can then see the files on the cd through the file system. Also, Brasero does not see the cdrom at all! However, if I boot with a cd preloaded then the cdrom operates normally, Brasero is happy, cd icon appears on desktop, bells ring & angels sing. My fstab entry reads:

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Is this normal unix operation, or is something wrong somewhere ?.

---

