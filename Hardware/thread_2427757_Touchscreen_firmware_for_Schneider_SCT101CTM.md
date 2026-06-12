---
title: "Touchscreen firmware for Schneider SCT101CTM"
date: 2019-09-25
forum: Hardware
---

### Post by gorbeich on 2019-09-25
Hi,

I've installed Ubuntu 19.04 on the tablet Schneider [SCT101CTM]("https://www.schneiderconsumer.com/en/product/2-in-1-full-hd-tablet/"). I've used [isorespin]("http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html") to attach a UEFI32 bootloader to the iso and then installed from usb. Everything works out of the box except the touchscreen and the sd card

To create a [touchscreen firmware for ubuntu]("https://github.com/onitake/gsl-firmware") it is required the firmware file from the stock windows installation (the windows touchscreen driver should work also). This file is named **GSL_TS_CFG.h** (or similar) or **SileadTouch.fw. **Unfortunately I've deleted the stock installation

Could possibly someone with the stock installation send me this file (or the windows driver) and I'll convert the firmware for linux

Thanks and regards

Edit: Got the firmware working in Ubuntu. See [https://github.com/dgatf/sct101ctm](https://github.com/dgatf/sct101ctm)

---

