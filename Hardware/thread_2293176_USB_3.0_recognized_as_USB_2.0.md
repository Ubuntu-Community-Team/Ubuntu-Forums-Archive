---
title: "USB 3.0 recognized as USB 2.0"
date: 2015-09-03
forum: Hardware
---

### Post by atkhan0072 on 2015-09-03
Hello,

I have bought a USB 3.0 Hub (Sitecom 071 ... ASMedia chip), that is correctly detected and working as a USB 3.0 in windows. However, In ubuntu it is always detected as USB 2.0 device. 

I have checked the 'lsusb' output,  and I can see USB 2.0 hub and USB 3.0 hub clearly. But everytime I stick it, it comes on the USB 2.0 hub, not USB 3.0. This can also be verified by running 'USB-Devices', where a normal sandisk USB 3.0 stick comes correctly at XHCI USB 3.0 device, but whenever I put the Hub back in, it comes as XHCI USB 2.0 device. Speed difference can also be seen.

Is there a way, I can force this device to be detected as USB 3.0 device ?

---

