---
title: "fixed device node for usb devices"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by poncenby on 2007-11-03
hello all,

i have a number of startup scripts which rely on a number of usb devices being on a certain /dev node.
How do I guarantee that my USB GPS receiver, for example, will always be on /dev/ttyUSB0? Even if it's unplugged/plugged in whilst booted?

I've look at /etc/udev/rules.d/*persistant but have had no luck, could anyone suggest a solution?

Many thanks

---

