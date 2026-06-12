---
title: "USB Issues With Upgrade from Ubuntu 18.04 to 22.04"
date: 2023-01-27
forum: Hardware
---

### Post by Curt Carpenter on 2023-01-27
I have some hardware (a digital oscilloscope) that works fine with Ubuntu 18.04 64-bit.  It requires a udev rule in /lib/udev/rules.d, and two initialization files in the /usr/local/share directory which should be executed when the rule is.

The hardware and software work fine with this configuration on Ubuntu 18.04 32- and 64-bit. but I cannot get them to work on Ubuntu 20 or 22.  Plugging the hardware into a USB port in 22.04 causes the OS to recognize the hardware (it appears in response to a terminal lsusb command), but handling the initialization files in /usr.local/share seems never to occur.   

Has there been some change in udev rule processing in the evolution from 18.04 to 22.04 that would make my udev rule for this device no longer work?  Any hints would be appreciated.

---

