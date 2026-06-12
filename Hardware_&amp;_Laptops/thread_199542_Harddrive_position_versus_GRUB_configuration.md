---
title: "Harddrive position versus GRUB configuration"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by bilange on 2006-06-18
Hi folks

For some reason I changed my Ubuntu hard drive from /dev/hdb to hda, and almost everything goes well.

The problem is, I needed to change my mountpoints in /etc/fstab, and also adjust my boot partitions in /boot/grub/menu.lst.

I made the changes, and everything is fine -- so far so good.

But, apparently everytime there's a new version of GRUB available for installing, grub goes back to its initial HDB setting, rendering the machine unbootable because my partition resides in hda. That machine hangs at "Mounting root [partition? filesystem?]", and finally dropping to a busybox shell.

I assume I missed something configuration-wise, forgot to tell GRUB or something else about my position change, but Im not sure. 

Any pointers?

Thanks :)

---

