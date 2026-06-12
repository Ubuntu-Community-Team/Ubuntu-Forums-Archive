---
title: "fglrx ATI Catalyst &quot; override refresh rate &quot; option not available"
date: 2009-10-23
forum: Hardware
---

### Post by josephdaniel on 2009-10-23
Hi,

First of all ,I know this is about the binary driver so it's not supported. I am just asking for your experience with it maybe someone can help me.

My new ATI Radeon HD 4350 is having some problems in Ubuntu 9.04. My CRT monitor supports 1024x768@85Hz and 1152x864@70Hz but they are not auto detected by the catalyst control center. On windows, I had an option to override the detection and use the refresh rates I specify. I can't find such an option in ubuntu. I tried entering the values manually in the xorg.conf but apparently they only take effect in the gdm. As soon as I login display is back to 60Hz which is the maximum auto detected value. 

I need to know how I can force ATI CC to use the higher refresh rates or at least not change what I have specified in xorg.conf.

Thanks in Advance,
Joe

Here's how my xorg.conf looks:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	HorizSync    30.0 - 69.0
	VertRefresh  50.0 - 120.0
	ModeLine     "1152x864_70.00" 96.8 1152 1224 1344 1536 864 865 868 900 -hsync +vsync
	Modeline     "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "IBM"
	Option	    "ModelName" "E74"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1152x864"
	Option	    "TargetRefresh" "70"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1152x864" "1024x768"
	EndSubSection
EndSection

```

---

### Post by josephdaniel on 2009-10-27
BUMP :s

---

### Post by josephdaniel on 2009-10-29
Solved by disabling Xrandr. fglrx now follows my xorg.conf modelines.

To disable XRandr, see ToeBee's post in this thread:
[http://ubuntuforums.org/showthread.php?p=8186465#post8186465](http://ubuntuforums.org/showthread.php?p=8186465#post8186465)

Hope this helps others.

Joe

---

