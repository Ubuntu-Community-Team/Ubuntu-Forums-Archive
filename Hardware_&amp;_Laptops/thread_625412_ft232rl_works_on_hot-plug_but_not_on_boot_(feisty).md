---
title: "ft232rl works on hot-plug but not on boot (feisty)"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by woodward on 2007-11-27
I am running feisty.  I have 2 sensors that use the ft232r chip.  On system boot /dev/ttyUSB0 and /dev/ttyUSB1 are created, cutecom can open the files, but no luck in communicating with the devices.  When I unplug the devices and plug them back in everything works fine.  Also, weirder yet, if I unplug and replug then restart the system, as apposed to shutting down and booting up, everything works fine again.

dmesg doesn't show any errors, 

lsusb -v, has the correct idVendor and idProduct (0x0403, 0x6001).

Any help is greatly appreciated.  It's a real pain to unplug and replug the sensors every time I turn on the computer.  The sensors are enclosed in the case and plug directly into the motherboard pins.

---

