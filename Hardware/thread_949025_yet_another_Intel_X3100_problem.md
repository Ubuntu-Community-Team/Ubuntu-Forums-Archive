---
title: "yet another Intel X3100 problem"
date: 2008-10-15
forum: Hardware
---

### Post by abc80 on 2008-10-15
Here's the deal. 

I have a laptop with ubuntu connected via vga to my lcd tv. In the display settings i set the resolution for the tv but the tv cant find any signal from vga. So i have to attach the vga cable to my macbook pro which does some automatic detection and the tv finds the vga signal so i switch back the cable to have my ubuntu view on the tv. I have to do this every time i turn off and turn on the tv if i want the image from the ubuntu laptop on tv. If i leave the macbook connected and turn off and turn on the tv it finds the computer just fine.

Is there anything i missed in xorg.conf?

This is my current xorg.conf

Section "Module"
	Load      "glx"
	Load      "GLcore"
	Load      "v4l"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
	Option "DevicePresence" "true"
	Option "ModeDebug" "boolean"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option "DPMS" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Depth   24
                Modes    "1920x1080@60" "1600x1200@60"  "1680x1050@60"  "1600x1024@60"  "1400x1050@75"  "1280x1024@75"  "1440x900@60"   "1280x960@60"   "1360x768@60"   "$
                Virtual 3200    1880
        EndSubSection
        Defaultdepth   24
EndSection


any ideas? the tv is a samsung le-37a656

thanks

---

