---
title: "XORG.conf"
date: 2008-11-28
forum: General Help
---

### Post by adamant715 on 2008-11-28
Why is almost all my stuff in this default? I did the setup thing in the terminal and that only asks for the Mouse and Keyboard. Nothing about Monitor and such.

Heres my Xorg.conf

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by andrewabc on 2008-11-28
This is the way xorg works now. My xorg is even smaller than yours.

Everything is autodetected. If you need to change something you have to manually enter it. I have done this for enabling my 5 button mouse.

The command you used does not work anymore for xorg. It did not work in Hardy.

---

### Post by jpeddicord on 2008-11-28
Moved to General Help, not desktop effects related.

---

