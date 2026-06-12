---
title: "why does ubuntu always mount my sd card as read only?"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by jang on 2005-08-22
I've tried this several times on my installed ubuntu hoary, it's always the same problem.  I've tried sudo chown username /media/usbdisk to no avail.  In contrast, when I connect sdcard onto an ubuntu livecd, it works without problems, I can read and write.  Any ideas?

---

### Post by PokerFacePenguin on 2005-08-22
Im no guru.....but I would begin looking at /etc/mtab and /etc/fstab and see what it says in there.

---

### Post by jang on 2005-08-22
/dev/sdc1 /media/usbdisk vfat rw,nosuid,nodev,sync,noatime,quiet,uid=1002,gid=1002,umask=077,iocharset=utf8 0 0

---

