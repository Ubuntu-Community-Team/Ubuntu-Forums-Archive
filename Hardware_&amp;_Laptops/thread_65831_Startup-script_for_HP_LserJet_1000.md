---
title: "Startup-script for HP LserJet 1000"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Ollan on 2005-09-15
I need to run the following command at startup.
"cat /opt/foo2zjs/sihp1000.img > /dev/usb/lp0"

The problem is that I get "Access denied" if i run the command in the terminal. Even if i write "sudo cat /opt/foo2zjs/sihp1000.img > /dev/usb/lp0". If i change the right to 662 for lp0 its possible to load the firmware to lp0 in the terminal.

How create a working script?

---

