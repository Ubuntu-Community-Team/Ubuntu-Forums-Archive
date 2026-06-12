---
title: "how do i system wide config hdparm for all my computers to extend life of hard drive?"
date: 2011-11-12
forum: Hardware
---

### Post by skinfish on 2011-11-12
how do i system wide config hdparm for all my computers to extend life of hard drive?

i need to use hdparm to check what hard disk options are usable to extend the lives of all my computer hard drives and apply them system wide.  

thank you

---

### Post by Toz on 2011-11-19
hdparm seems to be managed by udev these days (see */lib/udev/rules.d/85-hdparm.rules*). That script calls */lib/udev/hdparm* which sources */lib/hdparm/hdparm-functions* which parses */etc/hdparm.conf* for options. I would try editing */etc/hdparm.conf* for system-wide configuration.

---

### Post by skinfish on 2011-11-21
how can i tell what longevity and data safety features i can set on my sata2 drive?

thank you

Arthur.

---

