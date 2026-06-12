---
title: "How to make Ubuntu detect external display on startup?"
date: 2009-07-03
forum: Hardware
---

### Post by talava on 2009-07-03
Hello!

I've had an external monitor in use since Ubuntu 7.10, but my problems haven't yet been solved :)

The problem is, that my external monitor sometimes fails to light up when login screen should appear. Sometimes it takes several ctrl+alt+backspace -presses before I get login screen.

I assume this could be fixed by editin xorg.conf, but I've got no idea how.

Here's the oddly simplistic output:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by talava on 2009-07-03
Anyone?


The laptop in question is Acer 6292. Intel GMA 965-graphics chipset with X3100 3D acceleration.

The monitor is Acer X223W with a native resolution of 1680x1050.

---

