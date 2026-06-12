---
title: "Slow Graphics in kubuntu 8.10 with ATI Radeon 2400 HD"
date: 2008-11-10
forum: Hardware
---

### Post by alidm on 2008-11-10
I just installed a clean version of kubuntu 8.10 on my desktop, which uses RAID1 (mirror). Every time I booted the system, I couldn't see anything in graphical desktop (KDE), and my monitor kept saying "No Signal". I could, however, go directly to the shell (by Alt + Ctrl + F1) and login. I did some search on ubuntu forums and found out that the problem is with my ATI Radeon 2400 HD graphic card. So I followed the instructions on [this wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") page and then I could see my graphical desktop this time. Now everything is fine and the graphics is smooth and clear, though the only problem is that the graphics is quite slow. For instance, when I try to move a window through desktop, or scrolling a long document or webpage, the screen is being updated like every half a second, and it seems like my monitor refresh rate (frequency) is pretty low. My guess is that there might be something wrong with xorg.conf. Below is the content of my xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option      "VideoOverlay" "on"
	Option      "OpenGLOverlay" "off"
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
	EndSubSection
EndSection

```

Any help would be greatly appreciated.

--Ali

---

