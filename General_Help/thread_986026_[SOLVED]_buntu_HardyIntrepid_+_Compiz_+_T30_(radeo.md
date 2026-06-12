---
title: "[SOLVED] *buntu Hardy/Intrepid + Compiz + T30 (radeon 7500) = No GLXFBConfig"
date: 2008-11-18
forum: General Help
---

### Post by davient on 2008-11-18
I'm a relatively long time user of ubuntu (since breezy) I have in the past got beryl working on my t30.

I've not tried compiz for a long time and am now trying to get it to work under hardy. I've tried to follow all the advice in the many threads covering this topic (including [http://ubuntuforums.org/showthread.php?t=764633&highlight=7500]("http://ubuntuforums.org/showthread.php?t=764633&highlight=7500"))but am at a loss.

Another thread with a similar to this problem but poorly titled is at [http://ubuntuforums.org/showthread.php?t=969969&highlight=GLXFBConfig]("http://ubuntuforums.org/showthread.php?t=969969&highlight=GLXFBConfig")

Where I'm at:

Ubuntu Hardy Heron
IBM Thinkpad T30
Radeon Mobility 7500

Running a default xorg.conf (from dpkg --reconfigure)

using the script ```
./compiz-check.sh
```

from thread [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

gives :


```
Gathering information about your system...



 Distribution:          Ubuntu 8.04

 Desktop environment:   GNOME

 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

 Driver in use:         radeon

 Rendering method:      AIGLX



Checking if it's possible to run Compiz on your system...



 Checking for texture_from_pixmap...               [ OK ]

 Checking for non power of two support...          [ OK ]

 Checking for composite extension...               [ OK ]

 Checking for FBConfig...                          [ OK ]

 Checking for hardware/setup problems...           [FAIL]



There has been (at least) one error detected with your setup:

 Error: Laptop using radeon driver. 



```
So I choose yes to the following prompt 
```

Would you like to know more? (Y/n) y



 It has been detected, that you are running a laptop with an ATI chip.

 The radeon driver supports Compiz out-of-the-box but because of a nasty bug

 in the driver that causes X to freeze on some cards, this particular

 combination had to be blacklisted in Ubuntu "Hardy Heron".



 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is

 safe to skip the blacklist. 



Do you want to skip blacklist checks by Compiz? (y/N) y


```

Which adds SKIP_CHECKS=yes to ~/.config/compiz/compiz-manager

So now when I run 

```
compiz --replace&
```

which gives:

```
Checking for Xgl: [5] 20861

davient@thinkpace:~$ not present. 

Found laptop using ati driver. 

SKIP_CHECKS is yes, so continuing despite problems.

Checking for texture_from_pixmap: present. 

Checking for non power of two support: present. 

Checking for Composite extension: present. 

Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.

Checking for nVidia: not present. 

Checking for FBConfig: present. 

Checking for Xgl: not present. 

/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.

/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0

/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

So the error that is causing the problem appears to be No GLXFBConfig for default depth.

I have also tried installing the fusion-icon 

Anyone have any ideas?

I have also installed on a separate partition Ubuntu Intrepid Ibex to the same machine.  In this configuration I can actually run compiz but I get a white screen and cannot see anything. If I push alt-tab I can see the task switcher, but on switching all I get is white.

---

### Post by disneyfriedhistory on 2008-11-19
I too have a T30 and once had compiz working well wit the radeon 7500.  In fact, I'm running a T41, which also has a radeon 7500, on Hardy and it works well.  But Ibex hasn't worked well at all.  

Regardless of compiz, even metacity, without running it as a composite manager, works like crap. My FPS on glxgears is actually pretty decent - around 1500.  But dragging a window, or doing almost any gui interaction will cause it to drop below 1000.  I don't have any of these problems of my T41.  

I've actually had the ./compiz-check run properly.  But compiz gives a segmentation fault.  I've never seen this GLXFGConfig error.  But I don't usually use dpkg --reconfigure, but just edit xorg.conf by hand.  

The relevant info my current setup is:
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"radeon"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ATI Radeon"
	Vendorname	"ATI"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout"		"LVDS"			#LVDS = laptop
	Option          "AccelMethod"   	"EXA"			#Default = XAA; EXA should be better
	Option		"AGPMode"		"4"			#no default
	Option		"AGPFastWrite"		"true"			#Default = off
	Option		"EnablePageFlip" 	"true"			#Default = off
	Option		"AccelDFS"		"true"			#Default = off
	Option		"GARTSize"		"16"			#Card should be 16MB

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option		"AIGLX"		"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

```

This should at least give you results under Hardy.
Good luck!

---

### Post by davient on 2008-11-24
Thanks for that, it was close but not quite for me. I had a few more issues but I've now got everything working perfectly!

I found a post mentioning that compiz works perfect on knoppix, with a T30. I promptly got the latest cd version and put loaded up knoppix compiz :) 

It worked, so I grabbed the xorg.conf and I've now modified it to get to work under ubuntu.  Here is the minimal version for anyone else with this issue :)
```

Section "ServerLayout"
	Identifier     "Xorg"
	Screen      0  "T30 Screen" 0 0
	InputDevice    "Configured Mouse"
	InputDevice "Generic Keyboard"	
        InputDevice    "Synaptics Touchpad"
        Option         "AIGLX"     "true"
EndSection

Section "ServerFlags"
	Option "AllowMouseOpenFail"  "true"
	
EndSection



Section "Module"
# Comments: see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346408
	Load  "dbe" # Double Buffering Extension, very important.
	Load  "dri" # This shouldn't be available choice if user has selected driver vga, vesa or nv.
	Load  "glx" # GLX Extension.
	Load  "freetype" # Freetype fonts.
	Load  "type1"  # Type 1 fonts
	Load  "record" # Developer extension, usually not needed
	SubSection      "extmod"
		Option          "omit xfree86-dga"
	EndSubSection
EndSection

Section "Extensions"
	# beryl and compiz need this, but it can cause bad (end even softreset-resistant)
	# effects in some graphics cards, especially nv.
	Option "Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Section "Monitor"
	Identifier	"T30 LCD"
	Option	"DPMS"	"true"

EndSection

Section "Device"

	Identifier  "ATI Radeon 7500M"
	Driver      "ati"
	VendorName  "All"
	BoardName   "All"
	Option "GARTSize" "64"
	Option "AGPMode" "8"


	Option "XAANoOffscreenPixmaps" "true"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
EndSection

Section "Screen"
	Identifier "T30 Screen"
	Device     "ATI Radeon 7500M"
	Monitor    "T30 LCD"
	DefaultColorDepth 16
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"

EndSection

Section "DRI"
	Mode 0666
EndSection


```

I'm guessing this may also work in Ibex...?  I'll try this later and let you know :)

---

### Post by suffice on 2008-11-28
I am sorta getting the same problems with intrepid...thing generally work, but seem a bit flaky.....

makes wierd colors....i get segmentation fault errors runing firefox, gimp, and others......compiz was flaking out a bit so (menus dissapearing) and so i turned it off...just started to look for fixes now...

---

### Post by wandalalakers on 2008-11-28
I have a Thinkpad T30 that I'm configuring for a cousin.
Everything is working fine except I can't get any gl screensavers to start.
My screen just blanks out instead of displaying a screensaver.

---

