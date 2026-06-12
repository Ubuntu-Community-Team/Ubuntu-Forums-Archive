---
title: "Lexmark x125 installation: Translating RedHat to Ubuntu"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by Dr. E on 2005-12-23
I just got finished installing Ubuntu for the first time.  The only difficulty I am having is installing the printer drivers. Ubuntu correctly identified my Lexmark X125. I found the PPD files for my printer on linuxprinters.org and installed them. On linuxprinters.org it gives these special instructions for installing my printer, but it is for Red Hat users:


Because the driver needs to read status codes from the printer, this driver requires special setup which will be shown here for Red Hat systems, on other distributions it should work in a similar way. For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use. If your printer has locked up in the past, you may need to unplug it from the power outlet and plug it back in before this driver will work. If your printer is not connected to /dev/usb/lp0, you can specify a different device using the driver options.



Could someone please indicate how to achieve this in Ubuntu?

---

