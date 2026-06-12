---
title: "Is there a Linux driver for the Prolific PL-2305 usb2parallel adapter?"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by Steve Simon on 2005-08-02
Does anyone know of such Linux drivers (this is for connecting a USB port on a laptop to a parallel port on a HP LaserJet 1100)? Thanks.

---

### Post by blind0wl on 2005-08-11
Yeh, just type ```
modprobe pl2305
``` in a console and see how that goes....if it works let me know and I'll tell you how to add the module to bootup otherwise you'll need to type that everytime you want to use the usb.

Blindy

---

