---
title: "Will my USB Hub work in ubuntu?"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by SmashingPumpkin33 on 2007-12-21
Hello,

I just purchased a Nexxtech 7 port usb desktop hub with power adapter and would like to know if it would possibly work with my pc running Ubuntu as the OS. It says its plug and play. I would like to make sure it will work before opening it.

---

### Post by nickg on 2007-12-21
In general [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) is a good place to start to look up hardware compatibilities; however, you won't find anything about USB hubs there (unless my eyesight is failing me).

I guess the reason is that the USB communications protocols are so well understood and defined that the inter-operability is pretty much guaranteed within the standard linux kernel.

Certainly I have plugged a large variety of different USB hubs into different flavour Linux boxes and never once had any problems.

Top and bottom of it though is just plug it in and see. You can't damage the hardware (unless your machine is faulty to start with) and you are not going to initiate any changes in the core software. You should be able to see it by typing lsusb at a command prompt (might very well not come up as Nexxtech as they might very well have bought the harware in from a different manufacturer).

Peripherals plugged into the USB hub are a different matter and some are better supported than others.

---

