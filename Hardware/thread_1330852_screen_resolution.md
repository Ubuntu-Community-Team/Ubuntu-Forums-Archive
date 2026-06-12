---
title: "screen resolution"
date: 2009-11-18
forum: Hardware
---

### Post by 2handband on 2009-11-18
I'm trying out Debian but am posting my question here because I seem to get better help. I have an Acer laptop with one of those gotta-be-different 16" screens that requires a 1366X768 resolution. Ubuntu/Mint recognizes it right out of the box, but Debian does not and gives NO resolution options. I have an Intel Graphics Media Accelerator(GMA) 4500MHD video card. Here is my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"pc104"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection
```

Any help?

---

