---
title: "#Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;. X600 on Ubuntu 7.04"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by geeforce on 2007-06-27
Hi folks.

Just installed the latest driver via envy and starting glxgears produces that:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3308 frames in 5.1 seconds = 648.454 FPS
3277 frames in 5.1 seconds = 638.893 FPS
3277 frames in 5.1 seconds = 639.186 FPS
3277 frames in 5.2 seconds = 634.782 FPS
3164 frames in 5.0 seconds = 630.258 FPS
3277 frames in 5.1 seconds = 638.501 FPS

```

I don't know what to do now. Googling hasn't helped me so I'm desperate right now. Watching DVDs in nearly impossible because the video is slowing down massively :(

Here is the graphic section of my xorg.conf

```

Section "Device"
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

Might there be anyone who has solved this problem... Amen!

---

### Post by Baji on 2007-07-01
I got the same problem and fixed it by copying /lib/modules/2.6.20-15-generic/misc/fglrx.ko to /lib/modules/2.6.20-16-generic/volatile/fglrx.ko

and then running sudo depmod -a

and reboot

you can allways check if you still get the mesa error with fglrxinfo

---

### Post by RyCS42 on 2007-07-07
In addition to Baji's steps, I also ran the command sudo modprobe fglrx, after which the XFree86-DRI message was removed and glxinfo reported that I had direct rendering again.

---

