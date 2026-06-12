---
title: "How to install Creative NX Webcam in Ubuntu?"
date: 2010-12-18
forum: Hardware
---

### Post by crixtiano on 2010-12-18
Please, 

how to install creative nx webcam in Ubuntu? 

These are the informations I have:

> # lsusb | grep NX
Bus 003 Device 002: ID 041e:401c Creative Technology, Ltd Webcam NX [PD1110]

# uname -r
2.6.32-26-generic


So, what to do? I can't install the driver. What driver can I use? 

Thank you!

Cristiano M. Magalhães

---

### Post by IcarusR on 2010-12-18
It should just work, uses gspca_zc3xx & gspca_main modules which are built into the kernel.
Install cheese from the repositories & try it.

---

