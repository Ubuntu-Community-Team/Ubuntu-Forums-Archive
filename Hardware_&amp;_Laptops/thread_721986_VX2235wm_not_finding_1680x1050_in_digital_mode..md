---
title: "VX2235wm not finding 1680x1050 in digital mode."
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by tillywern on 2008-03-11
I'm trying to get my VX2235wm working in digital mode.   It works fine under analog mode but when I hooked up the DVI interface monitor is reported as having a max resolution of 1600x1200.

Here is an excerpt from the resultant Xorg.0.log.

(--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 at PCI:2:0:0:
(--) NVIDIA(0):     ViewSonic VX2235wm (DFP-0)
(--) NVIDIA(0): ViewSonic VX2235wm (DFP-0): 140.4 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic VX2235wm (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes
Section "Monitor"
    Identifier     "VX2235wm"
Horizsync       31.5-65.5
Vertrefresh     56.0 - 65.0
ModeLine  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
Option "PreferredMode" "1680x1050@60"
    Option         "DPMS"
 for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1440x1440"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1400x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

Here is the monitor stanza from my xorg.conf
Section "Monitor"
    Identifier     "VX2235wm"
    Horizsync       31.5-65.5
    Vertrefresh     56.0 - 65.0
    ModeLine  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    Option "PreferredMode" "1680x1050@60"
    Option         "DPMS"
EndSection

I'm wondering if the problem has to do with the fact that I changed ports on the back of my 5600.   Does this port have a different address?

---

### Post by root.user1 on 2008-03-12
Hi,

I have this same monitor on one of my desktop machines.  I'm getting 1680x1050 in digital mode.  Here's a chunk of my xorg.conf that Gutsy made for me during the install.

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7300 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

I'm using the latest restricted driver for the graphics card and haven't touched the xorg.conf file manually since I installed a couple of months ago.  I thought maybe my settings would be of help to you.

---

