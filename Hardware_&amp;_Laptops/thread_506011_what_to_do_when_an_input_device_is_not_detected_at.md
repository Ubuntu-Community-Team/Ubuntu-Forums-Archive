---
title: "what to do when an input device is not detected at all?"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by RawMustard on 2007-07-21
I have a panel pc here that runs Ubuntu magnificently; however the touch screen for it which is a zytronic capacitive projected screen connected to serial port com4 is not detected at all.
I cannot list this device in cat /proc/bus/input/devices - it doesn't show up in the hardware list either.

If I type cat < /dev/ttyS3 in a terminal, I can see data in the serial port when I touch the screen.  Now how to get that data to X?  Any tips for me pretty please?

---

### Post by bernied on 2007-07-21
In my understanding, if a device is not detected it means that ubuntu doesn't have a driver for it. So you need to find one (from the manufacturer, from google) and install it. This would normally take the form of a kernel module.

---

