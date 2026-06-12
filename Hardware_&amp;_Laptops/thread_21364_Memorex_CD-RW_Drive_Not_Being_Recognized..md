---
title: "Memorex CD-RW Drive Not Being Recognized."
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by Thief- on 2005-03-21
I just recently installed and internal CD RW drive, and Ubuntu did not recognize it when I booted up. The master and slave settings are correct, and windows recognized it fine.

Any help?

---

### Post by acascianelli on 2005-03-22
you probobly need dma enabled. run "hdparm /dev/cdrom", if you see that using_dma is off.  type in "hdparm -d /dev/cdrom" then see if you can detect your cdburner.

---

