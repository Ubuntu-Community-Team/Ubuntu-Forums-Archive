---
title: "Bluetooth Trouble  Toshiba Satellite A350 Phoenix BIOS - Jaunty"
date: 2009-05-07
forum: Hardware
---

### Post by mad.drivr on 2009-05-07
Hi All

I just received a Toshiba Satellite Fusion A350-X6310 and installed the Jaunty on it. Installation was smooth, enabled Compiz once i had installed the ATI Proprietary driver. But the Bluetooth never gets enabled. I have tried rebooting after using BT in Vista, i have tried a cold start but none seems to work. 

The machine has a Intel GM45 Express Chipset Mainboard, , ATI Mobile Radeon HD 3470 Graphics Chipset, 256-MB Dedicated Video RAM with Integrated Bluetooth v2.1 module.

I trid using Toshset but through various forums came to realize that the Toshset utility works only with Toshiba BIOS and not the Phoenix.

Any Ideas and suggestion

Thanks

P.S.: Absolute Beginner experience level with LINUX

---

### Post by mad.drivr on 2009-05-07
I Tried a: $sudo modprobe toshiba_acpi
The Result was:

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.28-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

---

### Post by davidmohammed on 2009-05-07
try the following [thread]("http://ubuntuforums.org/archive/index.php/t-316358.html")

---

### Post by Albert Que on 2009-05-09
I own a toshiba satellite A200 (phoenix BIOS) running ubuntu 9.04 (Jaunty Jackalope) and had the same problem. 
That worked to me:
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)

(search "Tim Richardson  wrote on 2008-07-08")

---

