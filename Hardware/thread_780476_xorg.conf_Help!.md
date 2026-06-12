---
title: "xorg.conf Help!"
date: 2008-05-03
forum: Hardware
---

### Post by Salpiche on 2008-05-03
Help! I have edited the xorg.conf file to reflect the correct resolution for my monitor 1024x768 with a refresh rate of 60 Hz, yet every time I reboot or restart xserver I still get the same options 50Hz or 55Hz which it is not the best for my monitor, now I ask! is my xorg.conf edited wrong? and if it is correct then why am I having this issue or if it wrong where did I made the mistake.

here I have attached the code on it. 

Before I am asked, I have done, with negative results :D
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and

```

sudo dpkg-reconfigure xserver-xorg 

```

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:0:15:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"MX50"
	Option		"DPMS"
	HorizSync	40-70
	VertRefresh	30-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"MX50"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by Zorael on 2008-05-03
Unless your monitor is saying that you're running 55hz or whatever, it's likely the nvidia driver playing tricks on you. It's a known bug.

---

### Post by starcannon on 2008-05-03
Instead of using a range for vert refresh, just set it to 60. That should fix you up.

---

### Post by Salpiche on 2008-05-03
> **starcannon said:**
> Instead of using a range for vert refresh, just set it to 60. That should fix you up.

as in?

```
Section "Monitor"
	Identifier	"MX50"
	Option		"DPMS"
	HorizSync	40-70
	VertRefresh	30-120
```

to

```
Section "Monitor"
	Identifier	"MX50"
	Option		"DPMS"
	VertRefresh	60
```

---

### Post by starcannon on 2008-05-03
Yeah that should do it, and I had forgotten, what Zorael said is true, there is a know bug with Nvidia driver, for instance, when you use the screen res gui in system preferences you'll see your refresh at say 55Hz but when you look at it in nvidia-settings it shows up at 60Hz.

I just use nvidia-settings.
```
sudo nvidia-settings
```
be sure to save settings before you exit.

---

### Post by Salpiche on 2008-05-03
> **starcannon said:**
> Yeah that should do it, and I had forgotten, what Zorael said is true, there is a know bug with Nvidia driver, for instance, when you use the screen res gui in system preferences you'll see your refresh at say 55Hz but when you look at it in nvidia-settings it shows up at 60Hz.

I just use nvidia-settings.
```
sudo nvidia-settings
```
be sure to save settings before you exit.

thanks, I forgot about ```
sudo nvidia-settings
```

either way it is set to auto, so I had to adjust to 60 manually, lets see if it keeps this time

---

### Post by Salpiche on 2008-05-03
Yup! that did it! thanks!!!

---

