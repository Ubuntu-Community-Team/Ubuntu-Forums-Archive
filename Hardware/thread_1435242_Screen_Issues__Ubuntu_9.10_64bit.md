---
title: "Screen Issues : Ubuntu 9.10 64bit"
date: 2010-03-21
forum: Hardware
---

### Post by godsgifttoearth on 2010-03-21
hi, looking for some help with my install.

when i boot and it gets past the bios i get a black screen with 2 horizontal lines across instead of the white ubuntu loading symbol. i then hear the noise for the long on prompt. i can then log in blind and get into my install.

the thing is this doesn't happen every boot. if i reboot the install a few times it will boot so i can see the log in screen and then log into the desktop which works.

my hardware setup is.....

samsung syncmaster 244t
7800gt (old style)
NVIDIA driver 195.36.15 (recently upgraded from 185 with no change)

i am using compiz desktop effects.

i am also 'using' a custom modeline with my monitor according to the manufacturer specs.

my xorg.conf looks like this

> Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
	Modeline "1920x1200_60.00" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
	Option         "DPMS"
	# 1920x1200 @ 60.00 Hz (GTF) hsync: 74.038; pclk:154 MHz
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

the monitor specs are....

WUXGA 1920x1200@60hz
horizsync - 74.038
vertsync - 59.950
pixel clock - 154mhz

horiz 30-81khz
vert 56-74khz

display area - 518mmx324mm

also according to my NVIDIA X server settings tab my screen size is detected wrongly. it says its 524mmx312mm.

my questions are....

[LIST]
[*]what is causing the lines at boot and the inconsistent boots?
[*]is my xorg.conf custom modeline correct?
[*]how do i change the display dimentsions?
[/LIST]

thanks for your help :)

---

### Post by godsgifttoearth on 2010-03-21
bump!

---

### Post by godsgifttoearth on 2010-03-22
bump!

---

