---
title: "How to write udev rules."
date: 2014-09-25
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2014-09-25
```
SUBSYSTEM=="usb", DRIVER=="usb", ATTR{idVendor}=="046d", ATTR{idProduct}=="c52b", ATTR{product}=="USB Reciever", ACTION=="add", RUN+="/usr/local/bin/mytouchpad disable"
SUBSYSTEM=="usb", DRIVER=="usb", ATTR{idVendor}=="046d", ATTR{idProduct}=="c52b", ATTR{product}=="USB Reciever", ACTION=="remove", RUN+="/usr/local/bin/mytouchpad enable"

```

These are what I have come up with. My goal is a script that fires when I plug or unplug my mouse. Script enables / disables the touchpad. These aren't working though. Any advice? Ubuntu Gnome 14.04

---

