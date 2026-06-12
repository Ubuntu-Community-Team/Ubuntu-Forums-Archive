---
title: "How to make Logitech trackball wheel scroll a full page instead of 3 lines?"
date: 2015-02-22
forum: Hardware
---

### Post by merlysys2 on 2015-02-22
I  recently migrated to Ubuntu from Windows. On Windows the device's (vertical) scrolling can be changed via a drop down box but no such thing shows up on Ubuntu System Settings -> Mouse & Touchpad.

I read that a file in /usr/share/X11/xorg.conf.d/ directory needs modification but that advice relates to the Logitech marble mouse. I don't know how to go beyond this, here are the files in there.
```

11-evdev-quirks.conf 
50-wacom.conf
11-evdev-trackpoint.conf 
51-synaptics-quirks.conf
10-evdev.conf 
50-synaptics.conf 
10-quirks.conf 
50-vmmouse.conf
glamoregl.conf
```

OS & trackball details: 
Ubuntu 14.04LTS desktop 
Logitech Cordless Optical Trackman
pic at [http://support.logitech.com/product/cordless-trackman-optical](http://support.logitech.com/product/cordless-trackman-optical)

---

