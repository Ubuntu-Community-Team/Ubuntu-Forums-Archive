---
title: "epson-printer-utility stopped working"
date: 2016-11-29
forum: Hardware
---

### Post by cscj01 on 2016-11-29
I have Ubuntu 14.04.5 x64 and an Epson Artisan 1430 printer.  I installed epson-printer-utility and escputil, and the printer has worked flawlessly since.  Suddenly today, espon-printer-utility quit with the following message:```
/usr/bin/epson-printer-utility

(epson-printer-utility:25603): GLib-ERROR **: Creating pipes for GWakeup: Too many open files

Trace/b/usr/bin/epson-printer-utility

```The program window appears, but it is not completely filled.  There are some black rectangles, and none of the icons or menu items are present.  I can find no reference to this message.  Does anyone have an idea of what may be happening?

---

### Post by cscj01 on 2016-12-18
I actually resolved this by rebooting.  My questions are, where does Ubuntu set the maximum number of open files, and what could be opening so many files?

---

