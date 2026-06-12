---
title: "Dell Laptop Issues"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by rshol on 2007-10-18
Running a Dell Latitude D820 Laptop with nVidia Quadro NVS 120M graphics card.  I have installed U7.10 and am running the provided nVidia drivers.  At work I use the laptop with a Dell docking station and a Dell 2007-wfp flat panel monitor.  When running the nVidia drivers I cannot get the external display to work, nor can I even configure a second display in the new display configuration utility.  When running the nv dirvers I have no problem with the second display.  

Any thoughts or can anyone point me to any material that may help?  This has, in my experience, been a long standing problem with Ubuntu, occurring in the last three versions.

---

### Post by Meson on 2007-10-22
Here is my xorg.conf, I have an almost identical setup as you:
```
Section "ServerLayout"
    Identifier     "layout0"
    Screen         "screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option	   "Xinerama" "false"
EndSection

Section "Monitor"
	Identifier	"monitor0"
    	Option		"DPMS" "true"
EndSection

Section "Device"
	Identifier     "device0"
	Driver         "nvidia"
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"monitor0"
    	DefaultDepth	24
	Option		"TwinView" "true"
	Option		"MetaModes" "nvidia-auto-select, nvidia-auto-select"
	Option		"TwinViewXineramaInfoOrder" "DFP-1, DFP-0"
	Option		"TwinViewOrientation" "leftOf"
	SubSection	"Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

#I've omitted my input devices to save space
```

I've found that this works docked or not.  My laptop screen is DFP-0 but also registers as CRT-1...?  Try it out!

---

