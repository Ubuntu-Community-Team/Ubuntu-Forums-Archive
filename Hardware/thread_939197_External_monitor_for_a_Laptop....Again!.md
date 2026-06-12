---
title: "External monitor for a Laptop....Again!"
date: 2008-10-05
forum: Hardware
---

### Post by franzmaximilian on 2008-10-05
Ok, there is already a lot of threads about this subject... but it seems that some of the difficulties encountered (and often solved!) by others are usually related to a specific laptop or GPU model or intended use.

So this is my problem:
when booting connected to an external lcd screen, my system is smart enough to switch off the internal monitor and use the external one. That is ok for my needs and I find it smart. 
Problems arise of course when trying to set the graphics to the size of my external LCD. All attempts and experiments where unsuccesful and many lead to a screwed xorg.conf (always have a backup at hand!!!)

My system: PackardBell MX51 series (Kubuntu runs flawlessly on it);
internal LCD 1280x800; nVidia geforce GO 6100.
Kubuntu 8.04 with KDE 3.5.10 and nvidia drivers, NO Compiz 
External LCD Asus VW 193D-B  1440x900  (55.935 Mhz hor. 60 Mhz vert. or 70.635 x 75) (NO DVI)

No way to have a 1440x900 screen on my external LCD. Nor System Settings nor nVidia Settings allow a choice larger than 1280x1024. 
My xorg.conf (only relevant sections displayed)follows below

Any suggestions?
Thank you for your attention
Franz

Section "Device"
	Identifier	"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Boardname	"nvidia"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1440x900@60"  106.47  1440 1520 1672 1904  900 901 904 932  -hsync +vsync
	Gamma	1.29	1.31	1.24
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1440x900@60"	"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

---

### Post by franzmaximilian on 2008-10-05
Now, this problem is solved and i feel stupid about it.
I didn't notice this line in Section"Screen": Virtual 1280 800
All that was needed was to change it into 1440 900

All right then?  No!  Another problem arises (from here?)

When I end my kde session, the screen turns black and X session freezes.
Only way to exit is to activate another session eg. Ctrl Alt F5, login there and shutdown.
I can live with it... but I definitely don't like it!

Any idea?

Franz

---

