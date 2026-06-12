---
title: "USB storage device issue"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by jqp on 2009-05-05
After upgrading from Intrepid to Jaunty, my USB memory sticks still work just fine.  However, my phone no longer works as a USB device.  My phone acts as a microSD card reader.  It connects to the computer as a "mass storage device".  Intrepid recognized it just like any other USB storage device I might plug in.  Jaunty doesn't.  What changed?

Same issue on home and work computers, both recently upgraded from Intrepid to Jaunty.

When I tell the phone to "disconnect" as "mass storage", the computer immediately recognizes the phone as a cellular modem (not a feature I use, but this worked before, and still works).

Any other common issues with SD card readers or similar devices since the upgrade?

---

### Post by rgenoud on 2009-05-06
try to load the usb-storage module:

```
sudo modprobe usb-storage
```

and then  plug your card.

if it works, you may want to add usb-storage to the file /etc/modules.

---

### Post by jqp on 2009-05-06
I tried this with no luck.  Other USB sticks still work, but still not the microSD-reading phone.

---

