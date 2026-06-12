---
title: "1024x768 Mode not working"
date: 2008-09-01
forum: General Help
---

### Post by Dudman on 2008-09-01
Hello all.

After searching around for a bit and finding a few solutions to my problem, i came out totally confused as to what to do or even what my problem was. I'm very new to ubuntu(and fairly new to linux).

My xorg.conf:
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

My output of "lspci | grep VGA"
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

When i try to switch to 1024x768, it either flickers & scrolls rapidly around the screen, or works well but takes up about 1/3 of my monitor(instead of all of it).

Thanks very much!

EDIT: Running hardy heron 8.04
EDIT: I Have updated the 109 initial files, and still nothing. Everything works fine in 800x600 mode, just not 1024x768.

---

### Post by steerguy on 2008-09-01
What brand is your graphics card? Nvidia? Have you enabled the binary drivers for you card? If not, go to Sytem>Adminstration>Hardware drivers and try enabling them, see if that helps.

---

### Post by Dudman on 2008-09-01
It's an intel card, 82845G/GL[Brookdale-G](see my first post).

In the system->admin->hardware drivers, there are two things that dont looks like video drivers, both are enabled.

One says HAL, the other one is for my network card..

-Dudman

---

