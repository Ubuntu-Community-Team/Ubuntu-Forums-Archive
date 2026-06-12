---
title: "Connecting touchscreen driver"
date: 2008-07-06
forum: Hardware
---

### Post by vdtdriver on 2008-07-06
I have a touchscreen developed by a private vendor and didn't have a driver for it.  Serial connection, so I went to the kernel driver section for the touchscreen.  Then modified the driver to match the output of the driver.  Modifications include generating absolute position events.  Now I would like to use the driver.  I have yet to figure out how to notify the kernel that the serial port attached to the touchscreen is to be connected to the driver.

I anticipate responses with suggestions on how to the connect X to the touchscreen.  I am not yet there.  Unless I connect the driver to the serial port there is nothing for the X server and X touchscreen driver (such as evtouch) to process.

---

### Post by vdtdriver on 2008-07-07
I also understand that udev is used to place devices into /dev.  I don't believe this addresses my problem either, although there are some parts of the "coldplug" feature of udev that I don't understand completely that might help.

---

