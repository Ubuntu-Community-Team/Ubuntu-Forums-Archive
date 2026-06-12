---
title: "Monitor loses signal if I turn it off"
date: 2008-09-08
forum: Hardware
---

### Post by dagoss on 2008-09-08
Whenever I turn off my monitor, when I turn it back on it says "no signal" like it would if the computer wasn't turned on.  I did a fresh install the same day I got this monitor.  It uses DVI output.  I'm not sure what to do.  This is really annoying since I have to restart the X-server to get the display back every time I need to turn of my monitor.

video card: Radeon 9600 XT
driver:  fglrx
KDE 4.1

---

### Post by dagoss on 2008-09-08
Fixed by adding the following the the Device section of xorg.conf

```

Option "MonitorLayout" "LVDS,TMDS"

```

Still using the non-free driver though.  I tried the Radeon driver, but it ran so slow that it was essentially unusable.  From what I understand, the driver only supports 2D with the 9600 model -- I suspect that KDE 4, with all its eye candy, was not pleased with that situation.

---

