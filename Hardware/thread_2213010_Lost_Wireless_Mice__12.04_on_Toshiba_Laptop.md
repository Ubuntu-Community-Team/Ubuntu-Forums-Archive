---
title: "Lost Wireless Mice / 12.04 on Toshiba Laptop"
date: 2014-03-24
forum: Hardware
---

### Post by pcar916 on 2014-03-24
I have used 12.04 on a Toshiba laptop for years with several wireless USB mice. After several months using only the touchpad, only two of three wireless mice will work. I've done nothing but 12.04 updates in the meantime.
[B]
Computer:[/B]
Toshiba Satellite A215-S4757
AMD Turion-64 X2
2GB RAM
Ubuntu 12.04 / Linux 3.2.0-60-Generic

**The USB mice that no longer work:**
1. Logitech notebook mouse (HID compliant) no model # found
2. Microsoft Wireless Notebook Optical Mouse 3000

**The USB mouse that works:**
1. Microsoft Natural Laser Mouse 6000
[B]
What I've done already to fix the problem.[/B]
I've tried the following:

1. Shutdown both the usbhid and usbmouse modules with sudo and without
modprobe -r usbhid            and 
modprobe -r usbmouse

There is no error message and I get the prompt back.

2. Unplug the mouse dongle and look at the modules still loaded:
mopdrobe -l usb*

shows the modules still there, and plugging the mouse dongle again does nothing.

How should I proceed with this troubleshooting procedure?

Thanks in advance

---

