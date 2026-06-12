---
title: "Xorg input device detection"
date: 2010-01-28
forum: Hardware
---

### Post by tfosdike on 2010-01-28
I recently bought a digital pen, and the manufacturer has kindly provided me with the old versions of their driver sources, which I have updated and all is now working on Karmic after explicitly adding the device to the Xorg configuration file.  However, I am having trouble finding how to get autoconfiguration working.

The xorg configuration file says that hald is used to autodetect hardware.  hald is apparently deprecated, and the documentation is not available.  Some threads on this forum suggest that udev is now used instead for Karmic, conflicting with the comments in xorg.conf.  Does anyone know what is the truth here?

If it is hald,  does anyone know where a copy of the documentation is archived?

---

### Post by tfosdike on 2010-02-03
I think I have found my answers.

The comment in the xorg ini file is correct but misleading.  I believe that hal is still available, but is not advised.  udev rules should be used instead.

Given that this the case, the best reference I have seen for writing udev rules for X11 drivers is:
[https://wiki.kubuntu.org/X/InputConfiguration](https://wiki.kubuntu.org/X/InputConfiguration)

---

### Post by tfosdike on 2010-02-04
This does not appear to work with the netbook remix, and the referred file 65-xorg-evdev.rules is not present on my system - will have to check versions.

---

### Post by Yellow Pasque on 2010-02-05
/lib/udev/rules.d/65-xorg-evdev.rules

It looks like so:
```
ACTION!="add|change", GOTO="xorg_evdev_end"

# By default, we use the -evdev driver for every mouse, keyboard, touchscreen
# or touchpad; later rules can then change the driver for specific input
# devices.
ENV{ID_INPUT}=="", GOTO="xorg_evdev_end"
ENV{ID_INPUT_MOUSE}=="?*", ENV{x11_driver}="evdev"
ENV{ID_INPUT_KEY}=="?*", ENV{x11_driver}="evdev"
ENV{ID_INPUT_TOUCHSCREEN}=="?*", ENV{x11_driver}="evdev"
ENV{ID_INPUT_TOUCHPAD}=="?*", ENV{x11_driver}="evdev"

LABEL="xorg_evdev_end"
```

EDIT: I'm on Lucid, so Karmic may not have this file because it still uses HAL.

---

