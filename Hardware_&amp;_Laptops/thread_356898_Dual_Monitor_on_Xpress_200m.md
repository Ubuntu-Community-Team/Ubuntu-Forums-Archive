---
title: "Dual Monitor on Xpress 200m"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by dano2769 on 2007-02-08
I have a toshiba satellite running ubuntu 6.1, and I want dual monitors. When I boot, only the external monitor works. I checked /var/log/Xorg.0.log and found this obvious error:
```
(WW) RADEON(1): Only one monitor detected, Second screen will NOT be created
```

How can I fix this? My xorg.conf is:

```
Section "Monitor"
	Identifier	"Laptop"
	Option		"DPMS"
	# HorizSync	28-64
	# VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Desktop"
	Option		"DPMS"
	# HorizSync	30-81
	# VertRefresh	56-75
EndSection

Section "Device"
	Identifier	"ati0"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ati1"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Screen		1
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"ati0"
	Monitor		"Laptop"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"ati1"
	Monitor		"Desktop"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead"
	Screen		"screen0"
	Screen		"screen1" LeftOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option 		"Xinerama" "true"
EndSection
```

---

### Post by woland on 2007-02-09
Did you try using aticonfig?
It worked for me.

The annoying part is, that you can't drag your application from one screen to another and there is no easy way to switch from single monitor to dual, just to restart gdm (Ctl+Alt+Esc). If your external screen is plugged in, then you get dual head, otherwise you get only one monitor.

---

### Post by pk_volt on 2007-02-11
I have a compaq presario 2650 with the x200m ati videocard

I'm trying to get dual head to work with my 17" lcd monitor.

I got the right resolution and all, but my 17" lcd doesn't display right

The bottom 1/4 of the screen replicates my laptop's top portion of the screen, and the rest of the 17" monitor is kind of fuzzy grey that seems to display portions of my laptop monitor

I can also see the mouse cursor on the edge of my 17" monitor when I move my mouse all the way to the right

can you post your xorg.conf or perhaps give me some pointers with aticonfig?

thanks!

---

### Post by woland on 2007-02-12
I've just reinstalled Ubuntu, so my xorg.conf wouldn't be of any help.
I will post when I'll try to mess with it again...

BTW, any luck with XGL on this card?

---

