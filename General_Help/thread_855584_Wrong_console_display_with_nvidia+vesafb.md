---
title: "Wrong console display with nvidia+vesafb"
date: 2008-07-10
forum: General Help
---

### Post by Pablo89 on 2008-07-10
Hi folks!
    I'm using nVidia GeForce 8400 GS graphics device, with "nvidia" drivers for X.org and "vesafb" for console, both configured to use my 1280x1024 screen resolution.
    However, there is a problem - proper display in console requires different monitor settings than X.org does! I mean, that the first sign of each line is out of the screen, and some places of console display are not sharp (that's how my LCD reacts for slightly different width).
    When I view some non-black picture in fbi and set my monitor to display it in the best way, consoles begin to look perfectly, but display in X.org becomes slightly moved and not sharp...
    Differences are slight, so I'm sure that the resolution is correct in both cases (I know X configuration, for vesafb I use "vga=0x31b").
    Does anybody else have similar problems? Any known solution/way to configure this kind monitor adjustment for X or console?
    Thanks in advance...

---

### Post by Pablo89 on 2008-07-25
I've managed to solve this by writing a correct "Modeline" to xorg.conf by hand. The only thing to notice that it's name could not conflict with Nvidia biuld-in names: so "1280x1024" was ignored, but "1280x1024_somestring" works a charm. "xvidtune" helped much :-).

From my new xorg.conf (values could be very specific for my hardware):

```

(...)
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline	"1280x1024_VGA" 108.88	1280 1331 1467 1696	1024 1026 1029 1066 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"NoLogo"	"True"
	SubSection     "Display"
		Depth	24
		Modes	"1280x1024_VGA"
	EndSubSection
EndSection
(...)

```

Hope it helps someone...

---

