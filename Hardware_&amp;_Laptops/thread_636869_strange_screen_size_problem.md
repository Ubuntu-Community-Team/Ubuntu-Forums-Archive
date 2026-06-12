---
title: "strange screen size problem"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by liquid77 on 2007-12-10
Hi , I have recently bought a new screen LG L225WS for my ubuntu PC But I have a problem with the screen size.The desktop is bigger than the screen so I cannot see the far left edge of my desktop.I have intsalled the proper driver for my Ati Radeon 9200 se and I have tried to configure the screen size with dpkg-reconfigure xserver-xorg and with ubuntu's screen-graphics dialogue.How could I solve this problem?

---

### Post by lian1238 on 2007-12-10
I think it's the monitor. Try adjusting the settings on the monitor itself. There should be an auto-adjust button. If not, try manually adjusting your monitor to fit your desktop.

---

### Post by liquid77 on 2007-12-10
I have tried to fix the problem with the monitor's menu but unfortunately I cannot change the size of the desktop so much tthat it fits the screen , neither manually nor automatically

---

### Post by lian1238 on 2007-12-12
I believe the optimum res for your monitor is 1680x1050. What is your screen resolution set as in System>Preference>Screen Resolution?

---

### Post by liquid77 on 2007-12-12
The resolution that i now use is 1680x1050.I have also tried other resolutions but the problem persists.Could that be a problem with the graphics card driver(I have an Ati radeon 9200 se with the linux driver installed)?

---

### Post by torabian02 on 2007-12-20
I have the same problem with an LG37LCD2 TV. Did you discover a fix for this Liquid?

---

### Post by mike_tyrell on 2008-02-02
ok this is my first time in trouble shotting some one else problem
what is the size of your screen and can you paste the out put of the command "xrandr" and a copy of your xorg file
:)
if your screen is LCD there is detect button in "system=Administration=screens and graphics" try that too it might help

---

### Post by jeremy on 2008-03-07
I have exactly the same problem with my LG L225WS, here are the relevant parts of my xorg.conf

Section "Monitor"
	Identifier	"L225W"
	Option		"DPMS"
	HorizSync	28.0 - 83.0
	VertRefresh	56.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G550 AGP"
	Monitor		"L225W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by jeremy on 2008-03-07
Ok, after some fiddling I have it working properly, the relevant parts of xorg.conf are now as follows...

Section "Monitor"
	Identifier	"L225W"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G550 AGP"
	Monitor		"L225W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1680x1050@75"	"1280x720@60"	"1920x1200@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

---

