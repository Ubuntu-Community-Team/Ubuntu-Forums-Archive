---
title: "epson usb scanner no longer recognized after upgrade to 10.04"
date: 2010-06-24
forum: Hardware
---

### Post by egstern on 2010-06-24
I have been scanning with my ancient Epson Perfection 636 usb scanner since days or yore, at least going back to Dapper.  I recently upgraded from Jaunty to Koala, and Koala to Lucid.  Since then, no scanning tool recognized my scanner.   Whenever I start scanimage -L, xsane, xscanimage or simple-scan, it cannot locate any scanner.  However, my scanner shows up in lsusb.

It turns out that the device was previously declared as a usb scanner in the file /etc/sane.d/epson.conf.  After the upgrade, I had to make the definition in the file /etc/sane.d/epson2.conf.

     egstern

---

