---
title: "lost 1680x1050 after use of external monitor"
date: 2009-11-16
forum: Hardware
---

### Post by anfractuosities on 2009-11-16
Im running Karmic, on an asus z96j notebook.  I connected a panasonic plasma tv as a second display via vga, and set the res of that moniter to 1280x720....

but now my laptop's screen res only goes up to 1360x 768 instead of 1680x1050...same thing using GUI and xrandr

---

### Post by anfractuosities on 2009-11-29
bump

---

### Post by coffeecat on 2009-11-29
Curious. If the external monitor is not connected, the xserver should autodetect the screen at bootup and set the resolution automatically.

In Karmic, there is not a /etc/X11/xorg.conf file by default. Usually, it is not needed. See if you have one - it's possible one was created when you configured the external monitor. The 1360x768 sounds like the natural resolution of your plasma screen. If you have, try renaming it to /etc/X11/xorg.conf.backup and reboot. Hopefully, the xserver will do a fresh probe of the hardware without relying on whatever is in xorg.conf.

If you don't have an xorg.conf then, sorry, I don't know.

---

