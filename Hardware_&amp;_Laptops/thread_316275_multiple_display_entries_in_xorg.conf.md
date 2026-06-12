---
title: "multiple display entries in xorg.conf"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by saintchuck on 2006-12-10
```
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 80.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Could someone tell me how to figure out which Monitor, Device and Screen I can remove?  I am hesitant to try commenting out any for fear of losing my display.  I have a Mobility Radeon adapter (one of the ones no longer supported by current ATI drivers) and assume this occurred when installing the 3PD drivers.  I do not/have not had an external monitor hooked up.

---

### Post by daou on 2006-12-10
You don't need to remove anything. The second monitor is probably for when you attach a second monitor to the laptop. You never know when you might need it.

But if you really want to remove it, you can try commenting out one monitor section and restarting x. If it fails to restart, you can still edit the xorg.conf file from command line:

```
sudo nano /etc/X11/xorg.conf
```

And when you have fixed the file, you can restart gdm which takes you to the Ubuntu login screen:

```
sudo /etc/init.d/gdm restart
```

---

