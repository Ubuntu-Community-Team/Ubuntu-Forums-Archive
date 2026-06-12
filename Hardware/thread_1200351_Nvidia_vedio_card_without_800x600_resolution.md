---
title: "Nvidia vedio card without 800x600 resolution"
date: 2009-06-29
forum: Hardware
---

### Post by sanz on 2009-06-29
Ubuntu8.04, Nvidia Quadro NVS 110M, proprietary driver enabled.

glx ok, 3d acceleration ok. default resolution 1280x800

for some reason, i NEED a resolution of 800x600 from time to time. unfortunately, there is no such a resolution available. 
(resolution adjusting dialog screeshot: [IMG]http://forum.ubuntu.com.cn/download/file.php?id=70347&t=1&sid=52ed244738d08b54573dbc2696f6671e[/IMG] 

relevant sections in Xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
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
Section "ServerFlags"
EndSection

---

### Post by sanz on 2009-06-30
after changing xorg, or "gtk-preconfigue xorg.conf", the resolution is changed to "800x600"/640x480, but not higher.

---

### Post by sanz on 2009-07-01
nobody has any hint?

---

### Post by overdrank on 2009-07-01
> **sanz said:**
> nobody has any hint?

Have you tried ```
gksu displayconfig-gtk
``` in Hardy 8.04?

---

### Post by sanz on 2009-07-03
Yes Hardy 8.04, video card as "nvidia quadro nvs110" and unknown 14.1" wide screen from Dell

already tried  sudo displayconfig-gtk, showing "Nvidia geforce 7 series" card and "plug 'n' play" screen. with same resolution value listed.

also tried here change screen to "lcd 1280x800", ended with only "800x600" and "640x480" available after reboot.

---

