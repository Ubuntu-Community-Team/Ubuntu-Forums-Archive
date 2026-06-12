---
title: "disabling side-scrolling on logitech mouse"
date: 2009-05-20
forum: Hardware
---

### Post by Sabru on 2009-05-20
I just upgraded to 9.04 from 8.04, and I think it's great that the developers finally added support for the side-scrolling wheel on my [logitech mouse,]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/191&cl=us,en") but the only problem is that now I don't want it. It's too easy to accidentally scroll to either side when pressing down the wheel, which makes Blender and Inkscape nearly unusable when shifting the view by middle-clicking.

Unless I'm mistaken, the best way to fix this problem is to REMOVE this functionality by editing the mouse section in my xorg.conf file. The only problem is that there appears NO SUCH section by default on my installation:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Could someone help me add a section for [this mouse]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/191&cl=us,en") so that the side-scrolling buttons are disabled? Any advice would be great, but I'd be exceptionally grateful to anyone who provides some copy-paste text that doesn't break X11...

---

### Post by Sabru on 2009-05-20
okay, nevermind! I just fixed the problem by messing around with 'xinput set-button-map' and reassigning buttons 6 and 7 to non-functioning values. Sorry for not figuring this out before posting this thread.

---

