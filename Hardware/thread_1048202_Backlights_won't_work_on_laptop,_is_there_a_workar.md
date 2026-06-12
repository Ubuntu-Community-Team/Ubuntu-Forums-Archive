---
title: "Backlights won't work on laptop, is there a workaround?"
date: 2009-01-23
forum: Hardware
---

### Post by Fzang on 2009-01-23
My brightness up/down buttons work and ubuntu displays as if my brightness is turned up or down... however, the screen brightness doesn't change a bit...

How can I fix this?

---

### Post by Fzang on 2009-01-24
Bumpin' up

---

### Post by jfr1tz on 2009-01-24
It helps if you can give a little more detail about your hardware.

---

### Post by Fzang on 2009-01-24
A Zepto Nexus A15 laptop:

NVIDIA® Geforce 9650M GT 512MB @ 1280x800
Intel® Core™ Duo-processor T3200
4096MB DDR2 800MHz PC6400
320GB SATA harddisk
Intel Wifi 533AN / ANBG / 450Mbit / Centrino 2

Motherboard ID: <DMI>
Motherboard name: Zepto Zepto
Chipset: Intel Cantiga PM45
BIOS type: Insyde
BIOS version: A15LL

---

### Post by bgerlich on 2009-01-24
This is a common problem with Nvidia 8/9 series cards, because the backlight brightness is governed by the graphics card itself. You'll have to install the newest nvclock [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/) and bind it to appropriate keys/acpi events.

You will find instructions how to do that here:
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)

---

