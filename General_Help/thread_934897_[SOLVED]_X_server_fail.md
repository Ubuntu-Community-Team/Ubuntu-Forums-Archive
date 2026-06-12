---
title: "[SOLVED] X server fail"
date: 2008-10-01
forum: General Help
---

### Post by CholericKoala on 2008-10-01
When I try to open a "New Login in a Window", a small window pops up and says "Cannot start new display"  "The X server failed.  Perhaps it is not configured well."

I used envyng to get my nvidia driver for my 8800gt and all is well with compiz and general video stuff.

Any insight as to what I need to do to get my x server to cooperate would be of help.  Thanks.

My xorg.conf is as follows:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


--------------------------------------

Actually, I found that all I needed to do was install "xnest" through the package manager.

---

