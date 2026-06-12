---
title: "problems with ATI Raedon 9600 Pro + compiz-fusion"
date: 2008-07-20
forum: Hardware
---

### Post by aaronp on 2008-07-20
Hi all,

I installed a new Raedon 9600 Pro (AGP8) last night. Had a few different attempts at getting the fglrx driver working and finally got it to 'say' that it was working (in 'Hardware Drivers' it says that the ATI accelerated driver is enabled and in use)

I can get all of the Compiz Fusion effects to work ok so assumed it was ok but frequently on random things (moving a window, opening a new window, changing desktops etc.) I get badly rendered multi-colour triangle in the top right quarter of the screen. Sometimes this will just stay there for a bit and recover but other times it just gets worse and starts to cover the whole screen until I Ctrl-Alt-Backspace and login again.

Output of 'fglrxinfo' says MESA so I'm wondering if this is causing the problem or if it is something else:

```

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

```


Here is my xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Any ideas?

thanks
Aaron

---

