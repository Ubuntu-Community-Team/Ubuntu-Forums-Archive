---
title: "[SOLVED] Panasonic CF-19"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by BoomerET on 2007-10-04
Have searched thru forums here and found nothing specific to my setup.

Have a Panasonic CF-19 Toughbook.

It does not have a touchscreen, but does have the digitizer.
(Touchscreen you can use a finger, Digitizer you have to use the pen).

I've tried the LiveCD for both Edgy desktop and Feisty desktop.

The digitizer works fine in Ubuntu 6.06 (Edgy), and when I look in /proc/bus/usb/devices, the usbhid driver is being used.

The digitizer does not work in 7.07 (Feisty).
It lists the driver as none.

Did the linuxwacom group screw this up for me?
(The digitizer on the CF-19 is a wacom, as we had one come back that had been run over by a backhoe, so I tore the thing apart to see what all the components were)

Here's the background...

Have about 1000 of these units in the field, so recompiling the kernel is not an option, however replacing a file/driver/library and rebooting the machines is.

The 500 or so CF-18 units we have work fine, just the CF-19's don't work.



Boomer

---

### Post by BoomerET on 2007-10-05
Looked through changelogs for kernels.

Seems ALL wacom devices were blacklisted in hid-core.c as of 2.6.18

Commented out code to blacklist, recompiled modules - working again.

Thanks go out to Mr. Cheng from Wacom for helping sort this out.



Boomer

---

### Post by elect on 2007-12-08
Hey Boomer, can u tell me how did u resolve for cf-18? 

My touchscreen is not calibrated...

---

