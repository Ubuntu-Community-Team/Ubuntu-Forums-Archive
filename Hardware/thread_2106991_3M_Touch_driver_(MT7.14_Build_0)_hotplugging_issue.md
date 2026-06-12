---
title: "3M Touch driver (MT7.14 Build 0) hotplugging issue in Ubuntu 12.4"
date: 2013-01-20
forum: Hardware
---

### Post by tpope on 2013-01-20
While migrating our kiosks (which use the 3M C2254PW multi-touch displays) to Ubuntu 12.4, I ran into an issue with the 32-bit MT7.14 Build 0 touch screen drivers, where touch input would fail after disconnecting and reconnecting the touch input device (i.e. either turning the monitor off and on again, or unplugging and plugging back in the USB cable).  After a few hours of digging around the installation files and system logs, I managed to narrow down the problem and fix it.

Basically, the udev rule which the installation script copies into /etc/udev/rules.d uses deprecated syntax; replacing BUS with SUBSYSTEM, and SYSFS with ATTR, seems to resolve this.  I also had to create an additional rule which restarts TWDrvStartup in order to bring touch input back up when the touch input device is reconnected.

The attached patch should work on the default server installation of Ubuntu 12.4.  Hope this might help someone out.

---

