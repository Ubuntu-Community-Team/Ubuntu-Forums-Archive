---
title: "[SOLVED] Ubuntu Thinks My Hard Drive is a CDROM"
date: 2009-01-01
forum: Hardware
---

### Post by f37u5g0d on 2009-01-01
I used unetbootin to install ubuntu 8.04 on my acer aspire one and now ubuntu thinks that my windows xp partition is a cdrom drive!  It is mounted in /media/cdrom0.  When I try and open it up in computer it says "cannot mount, invalid mount options."  I think it happened in the first place because unetbootin makes the kernel think that the ntfs partition is a CDROM drive so that you can boot the live cd iso without a cd drive.  How can I fix it?

---

### Post by f37u5g0d on 2009-01-01
I went in and edited my /etc/fstab.  I changed my mount point to /media/windows (and created that directory) and I changed the options to defaults (with noauto) for my ntfs partition.  Now it works like a charm!

---

