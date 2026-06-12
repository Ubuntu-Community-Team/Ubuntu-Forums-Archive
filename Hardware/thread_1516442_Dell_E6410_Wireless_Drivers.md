---
title: "Dell E6410 Wireless Drivers?"
date: 2010-06-23
forum: Hardware
---

### Post by CaseyC on 2010-06-23
I loaded my laptop which is a Dell E6410 i5 4gb ram with Ubuntu 9.10 since the latest edition would not install. I basically have everything working but the bluetooth and the wifi. Also the only way that i can boot into the GUI is to disable multiple cores and only have 1 core running, but if i could get my WiFi working as of now that would be awesome!

Anyone have any ideas on how to find this driver?

---

### Post by waynefoutz on 2010-06-23
Why would you want to run with one core shut down?

You might have better results overall by going with 10.04 64 bit.

To find the driver, plugging it into the router with a hard wire, open up synaptic, hit reload, then go to System/Adminstration/Hardware drivers works about 90% of the time.

---

### Post by xiaoqi on 2010-06-26
Good hints. But not working in my machine.

I've followed this steps in my new E6410 with 10.04.

After you did "reload", and when refreshing the Hardware Drivers, the wireless card driver is popup as one reminding, with following text:

===START===
No proprietary drivers are in user on this system.

Proprietary drivers do not have public source code that Ubuntu developers are free to modify. Security updates and corrections depend solely on the responsiveness of the manufacturer. Ubuntu cannot fix or improve these drivers.

Broadcom STA wireless driver

  Tested by the Ubuntu developers.
  License: Proprietary

These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.

===E N D===

Click "activate", but the installation is failed.

Error Message as below --

"Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log".

The last two sections in "jockey.log" are:

... ...
WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver.
DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted.
======

What that mean? Is our Ubuntu 10.04 doesn't support this hardware? 

Please help to check, thanks.

---

