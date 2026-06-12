---
title: "Wacom Intous 3 tablet not working anymore"
date: 2016-04-19
forum: Hardware
---

### Post by Dread Knight on 2016-04-19
Heya! I have an Intuos 3 A5 and for about 1-2 months now it's not working anymore.

> lsdread@FreezingMoon:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0c76:160c JMTek, LLC. 
[B]Bus 003 Device 002: ID 056a:00b1 Wacom Co., Ltd Intuos3 6x18
[/B]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dread@FreezingMoon:~$ 



It's being detected, the LED is on, but stylus and buttons are not working. Been on Ubuntu 15.10 64bit, recently upgraded to 16.04 hoping it would fix it, but no luck. I've even tried changing the USB port....
Any help appreciated! Thanks!

> xserver-xorg-input-wacom is already the newest version (1:0.32.0-0ubuntu3).


---

### Post by mörgæs on 2016-04-20
Does it work in a live boot of 16.04?

---

### Post by Dread Knight on 2016-04-20
> **mörgæs said:**
> Does it work in a live boot of 16.04?

I gave an USB drive a try yesterday and it wasn't working, but yet again I don't recall if it was working that way previously. Will try again soon and see if the driver was actually installed to begin with.

---

### Post by Dread Knight on 2016-04-20
Perhaps some wires within the cable got severed, sigh :(

---

