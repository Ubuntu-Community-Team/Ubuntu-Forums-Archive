---
title: "Power usbstrip off in 12.04"
date: 2012-11-25
forum: Hardware
---

### Post by bendt.v.rasmussen on 2012-11-25
Is it possible in 12.04 to power off the +5v of the usb in order to control a 110v/220v usb power strip?

---

### Post by 2F4U on 2012-11-25
As far as I know, the USB devices in Ubuntu are configured to automatically go into powersave if no devices are connected:

[http://azitech.wordpress.com/2008/11/27/usbcore-autosuspend/](http://azitech.wordpress.com/2008/11/27/usbcore-autosuspend/)

Why would you want to completely power USB off?

---

### Post by bendt.v.rasmussen on 2012-11-25
I have a "power strip", that can turn off 220v devices. It has no digital logic inside, but just turns on, when it detects +5v from the usb. It would be great if I could control this from command line, so that I could make my server turn on and off equipment.

---

