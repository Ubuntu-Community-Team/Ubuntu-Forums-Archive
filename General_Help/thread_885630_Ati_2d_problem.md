---
title: "Ati 2d problem"
date: 2008-08-10
forum: General Help
---

### Post by Borsook on 2008-08-10
Default drivers did not allow me to use some refresh rates etc so I installed ATI drivers, first via the repositories then Envy. Unfortunately now (although the precious problem is gone) when I e.g. move windows the screen does not refresh properly, various "artefacts" are left until I move a mouse cursor over them. If it matters I have a Radeon 9600 card and I'm using Ubuntu 8.04. I'd be grateful for any help.

---

### Post by Yellow Pasque on 2008-08-10
Try generating a mode line with cvt and pasting it into the Monitor section of /etc/X11/xorg.conf
Example:
```
cvt -v 1280 1024 60.0Hz
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

gksudo gedit /etc/X11/xorg.conf
```

Make sure you change the '_' to a '@'
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	**Modeline "1280x1024@60"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync**
EndSection
```

---

### Post by Borsook on 2008-08-10
thanx, I'll try that.

---

### Post by Borsook on 2008-08-11
Sadly this did not help at all...

---

