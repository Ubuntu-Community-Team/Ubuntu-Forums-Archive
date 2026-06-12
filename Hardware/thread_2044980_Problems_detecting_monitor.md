---
title: "Problems detecting monitor"
date: 2012-08-20
forum: Hardware
---

### Post by coeus82 on 2012-08-20
I'm on Ubuntu 12.04 64 bit and I'm using an Acer z5610 which is an All-In-One.

**Problem:** Xserver is unable to detect my monitor, lightdm fails. Whatever Ubuntu set as the default XORG configuration, it is wrong. 

So I did a `xrandr -q` to see what display options I have and I get the following:

```

VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      59.6*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  

```

From this, I decided to create my own xorg.conf and it looks like this:
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "LVDS1"
EndSection

Section "Monitor"
	Identifier   "LVDS1 Monitor"
	Option			"DPMS"
	HorizSync       28-51
	VertRefresh     43-60
EndSection

Section "Monitor"
	Identifier   "VGA1 Monitor"
	Option        "Ignore" "1"
	HorizSync       28-51
	VertRefresh     43-60
EndSection

Section "Device"
        Identifier      "Integrated Graphics Chipset: Intel(R) G45/G43"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "LVDS1"
	Device     "Integrated Graphics Chipset: Intel(R) G45/G43"
	Monitor    "LVDS1 Monitor"
	DefaultDepth    24
	SubSection "Display"
			Depth           24
			Modes           "1920x1080" "1680x1050" "1600x1024" "1400x1050" "1280x1024" "1440x900" "1280x960" "1360x768" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "VGA1"
	Device     "Integrated Graphics Chipset: Intel(R) G45/G43"
	Monitor    "VGA1 Monitor"
	DefaultDepth    24
	SubSection "Display"
			Depth           24
			Modes           "1024x768" "800x600" "848x480" "640x480"
	EndSubSection
EndSection

```

LVDS1 is what I want because it's what supports the 1920x1080 resolution. 

LightDM still does not work, but installing GDM worked! So the above Xorg configuration fixed my display issues, but I need to use GDM to get in. When I try to use LightDM, I get the following error message in the logs:

```

Fatal server error:
no screens found

```

For some reason, LightDM is not detecting my screens. All of this seems to stem from bad support for my monitor. Looking for any help on why Ubuntu isn't properly detecting my monitor (leading me to create my own xorg.conf) and how I'm able to get LightDM to detect my screens.

---

