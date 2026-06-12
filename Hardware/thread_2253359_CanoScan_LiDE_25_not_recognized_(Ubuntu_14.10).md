---
title: "CanoScan LiDE 25 not recognized? (Ubuntu 14.10)"
date: 2014-11-19
forum: Hardware
---

### Post by eezacque on 2014-11-19
My CanoScan LiDE 25 is listed through 'lsusb', it is detected through 'sane-find-scanner'.
However, it is rarely detected by 'Simple Scan', and when it is detected it doesn't scan, and never detected through 'xsane'.

Any clue?

---

### Post by eezacque on 2014-11-19
Fixed by disabling xHCI in BIOS

---

### Post by wonko on 2014-12-20
Awesome! Thank you for this :) (Same scanner, same problem, Skanlite in Kubuntu 14.10).

---

### Post by johnaaronrose on 2015-08-28
My CanoScan LIDE 25 scanner used to be recognised (& scan OK) by Simple Scan & XSane until recently: I don't know exactly when as I don't often use it. Now it's not even recognised by either app. However, my HP Deskjet Printer/Scanner is recognised (& scans OK) by XSane but not by Simple Scan. I have a 4 year old desktop without a USB 3.0 socket i.e. only with USB 2.0 sockets. I don't see any xHCI setting in the BIOS. I do see aHCI for the SATA drive but I presume that is not related to xHCI. Any ideas?

---

