---
title: "Nvidia install problems"
date: 2008-09-02
forum: Hardware
---

### Post by Kalith on 2008-09-02
Ok im a relative noob to ubuntu.Everything apart from my 9600gt setup fine after install,first i had to get my refresh rate and resolution back via xconfig and now im recieving this error with the command glxinfo.

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

I looked around and it seems someone said a fix was to disable composite in the xconfig file,but as you can see here in my file.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
        SubSection "Display"
        Depth        24
        Modes      "1280x1024_72.00"
        EndSubSection

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
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"pc105"
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
        HorizSync     64-80
        VertRefresh   60-77
        Modeline "1280x1024_72.00"  132.75  1280 1368 1504 1728  1024 1025 1028 1067  -HSync +Vsync

EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

It already is,i have tried installing and uninstalling,nothing works.Im installing the nvidia drivers etc via EnvyNG.Any help appreciated.

Thankyou

---

