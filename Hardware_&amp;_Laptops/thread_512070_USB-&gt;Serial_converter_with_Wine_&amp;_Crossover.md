---
title: "USB-&gt;Serial converter with Wine &amp; Crossover"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by john8791 on 2007-07-28
I installed MapSend Topo 4.20d with the eval version of Crossover.  It works great with my Magellan SporTrak Map GPS.  Even uploads maps find via the serial port.

My problem is I would like to use my Belkin USB-> serial converter with it so I don't have to unplug my modem each time.  When I plug it in and check with dmesg, it seems to be detected and says it is /dev/ttyUSB0.  I verified it with "ls /dev" and lsusb.  I read somewhere to make a symlink in the ~/.cxoffice/<bottlename>/dosdevices/ directory to "com1" (or whatever com port),  but this does not make a difference.  Any ideas?

Thanks

---

