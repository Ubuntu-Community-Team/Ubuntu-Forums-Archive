---
title: "Catalyst flickering? (2048x1536 CRT)"
date: 2009-03-08
forum: Hardware
---

### Post by dh003i on 2009-03-08
I did an install of 64-bit Kubuntu 8.10 Desktop, and by default the resolution was 800x600. Strange, since I have a 3-megapixel 2048x1536 Sony GDM-F520 CRT; and Sabayon at least installed Catalyst and got me to 1600x1200 without problems.

So, I used EnvyNG-QT to install the Catalyst drivers; it seemed to work. I rebooted, and the login screen comes up. So far so good -- the resolution is clearly much higher, probably 2048x1536 (but I can't tell from sight).

Then I login and the screen is flickering ridiculously; sometimes it's immediate, sometimes it takes a while. But when the flickering starts, I can't do anything with it except move the mouse. If I click on the KDE menu button, maybe it eventually shows up a minute later. And the panels get resized and messed with when the flickering starts. 

How can I fix this? I've read of similar problems when Compiz is enabled; but how can I terminate it? 

**Result of [COLOR="SeaGreen"]compiz-check[/COLOR]:**

> xprop: unable to open display '''
Desktop Environment: Unknown
Graphics cip: ATI Technologies Inc RV730XT [Radeon HD 4670]
Driver in use: fglrx
xvinfo: Unable to open display
xdpyinfo: unable to open display "".
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [FAIL]
Checking for non power of two support... [FAIL]
Checking for composite extension...xpdyinfo: unable to open display "". [FAIL]
Checking for FBConfig... [FAIL]
Checking for hardware/setup problems.../usr/bin/xset: unable to open display ""
Error: unable to open display (null)
Error: unable to open display (null)
  [SKIP]
At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use.


This is puzzling since the [X.Org Wiki - Radeon Program]("http://wiki.x.org/wiki/RadeonProgram") webpage says that the R700 ATI GPU's have "platinum" support for Compiz.

**My [COLOR="Green"]xorg.conf[/COLOR] file:**

> Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	#Disable	"dri2"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver	"fglrx"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection


**My hardware:**
MB: Asus P5Q-E
HD: WD 1TB Black
RAM: 8GB DDR2-800
CPU: Intel Q9550
GPU: Radeon HD4670

**PS:** Argh...Catalyst sucks. When will radeonhd support more than modesetting for the 4670?

---

### Post by dh003i on 2009-03-09
anyone have any ideas on how to troubleshoot this?

---

### Post by dh003i on 2009-03-16
Ok, I installed GNOME ([COLOR="DarkGreen"]sudo apt-get install gnome[/COLOR]) and GNOME seems to work fine. The failsafe also seems to work fine. Now, KDE seems to work "ok". It still flickers occasionally. Also, GNOME flickers when I open the ATI Catalyst Control Center; but at least now it is usable. 

The flickering seems to be random; and it seems to slow down my computer. 

What is going on? 

Maybe I should install the radeonhd drivers? 

Oh, also, here's how my xorg.conf looks (I haven't looked to see if it changed or not, but either way this verifies):

```
Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	#Disable	"dri2"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver	"fglrx"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection
```

---

### Post by markbuntu on 2009-03-18
Does Catalyst report your monitor correctly when you use the detect monitor option?

What does your Xorg.0.log have to say about that?

---

