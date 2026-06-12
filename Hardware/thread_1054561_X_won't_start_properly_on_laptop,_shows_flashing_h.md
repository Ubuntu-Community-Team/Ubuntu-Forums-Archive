---
title: "X won't start properly on laptop, shows flashing horizontal lines instead"
date: 2009-01-29
forum: Hardware
---

### Post by Niktavalos on 2009-01-29
I installed and booted into Ubuntu, but I can't get the GUI to show up.  When it boots naturally, I get nothing but a bunch of flashing horizontal lines, but I still know it's booting because it plays the startup chime.  When I interrupt it to go to command line and try startx, I get something like this:

VESA: no valid modes
Screens found, but none have a usable configuration

Fatal server error
no screens found
giving up

This is on an ASUS laptop with Radeon 3650M video.

Edit: I tried changing between VESA and ATI driver in xorg.conf, same results.

---

### Post by IQRules on 2009-01-29
Google envyNG, try install that.

Or go to safemode, remove /etc/X11/xorg.conf file first.

---

