---
title: "DELL D610 W/ 915GM Video - Still limit resolution"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by samjaynes on 2007-02-28
I need your help and advice.  I have googled, and read as much as I could before posting to this forum.  As noted, I have the Dell Lattitude D610 (Ubuntu Edgy Eft) with the 915GM Video Card.  I am limited to just 1024x768 resolution.  Here are the steps I have done so far:

Installed 915resolution 
Per thread: ([http://ubuntuforums.org/showthread.php?t=354666&highlight=915gm](http://ubuntuforums.org/showthread.php?t=354666&highlight=915gm))
sudo apt-get install 915resolution
sudo dpkg-reconfigure xserver-xorg
restarted xserver, but wouldn't come back from ctl-alt-f7, but ctl-alt-f1 went to a session.

Per this thread: ([http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution))
I edited 915resolution MODE 30 to 1280 1024 32 (not being too picky at this point)
Changed the default to use mode 30 xres to 1280 yres to 1024 and bit to 32

Here is a some text from /etc/x11/xorg.conf:
> 
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics
Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics
Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection




At this point, I am only allowed to select 1024X768 or 800X600 in System/Preferences/System Resolution...  what am I missing? 

Is their a repository that I am missing, driver, xorg stuff???  Any assistance would be helpful, I have seen quite a few threads both in Ubuntu forums, and other linux forums.

---

### Post by samjaynes on 2007-02-28
Just to add, the /etc/default/915resolution is:

> 
MODE=30
XRESO=1280
YRESO=1024
BIT=32


Again, any assistance would be -greatly- appreciated.

---

