---
title: "Internal zip 250 install woes. . ."
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by krpnm on 2006-07-10
Hi,

I can't seem to get my zip drive (a) recognized and (b) mounted.

I have:

a.  sudo lshw -C disk (shows the zip as hdb)
b.  Created a new mount point (/media/zip0)
c.  Added the zip to the /etc/fstab (/dev/hdb4	/media/zip0	vfat,auto defaults,user,noauto	0	0)
d.  There is an hdb entry in /dev
e.  Am using Xubuntu v6.06

When I sudo mount -a (restarting the fstab) I get a "line 11 in /etc/fstab is bad."

Can someone in the know help me out?

---

