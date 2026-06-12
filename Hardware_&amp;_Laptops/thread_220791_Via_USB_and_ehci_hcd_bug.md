---
title: "Via USB and ehci_hcd bug"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by cedced on 2006-07-22
Carrying over to this thread a problem initially discovered on Breezy Badger as it's still current.

Summary:

USB devices not working. VIA hardware with 2 USB controllers, one for USB 1.1 and one for USB 2.0. Conflict between ehci_hcd and uhci_hcd modules. 'modprobe -r ehci_hcd' as a temporary fix: but will only support USB 1.1, not USB 2.0.


Full bug report and comments :

[http://www.ubuntuforums.org/forumdisplay.php?f=102](http://www.ubuntuforums.org/forumdisplay.php?f=102)


As far as I'm concerned, this bug was introduced a few kernel revision ago on Dapper Drake. But as the linked thread suggests it, it happened to some people using Breezy Badger as well.

---

### Post by uffez on 2006-07-22
I am new to Ubuntu, but also a bit confused. I downloaded and ran the live-CD- there USB2.0 was supported. But, when i did the actual desktop installation it no longer works...

/Uffe

---

