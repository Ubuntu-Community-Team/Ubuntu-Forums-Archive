---
title: "LIRC modules on 2.6.17-10-386"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by tari on 2007-01-27
I just installed nVidia drivers for my card, and it changed my kernel from 2.6.17-10-generic to 2.6.17-10-386.  However, now I cannot load the lirc_mceusb2 module for my remote control.
[quote="sudo modprobe lirc_mceusb2"]
WARNING: Error inserting lirc_dev (/lib/modules/2.6.17-10-386/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_mceusb2 (/lib/modules/2.6.17-10-386/misc/lirc_mceusb2.ko): Invalid module format
[/quote]
I built this with LIRC 0.8.1, and it works perfectly with 2.6.17-10-generic (with a module built for that kernel, of course), but building the module in the 386 kernel won't work.  Until I can solve this, I'm stuck without direct rendering (using the generic kernel).

---

