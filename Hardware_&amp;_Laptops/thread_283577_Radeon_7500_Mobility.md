---
title: "Radeon 7500 Mobility"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by spoon13 on 2006-10-24
Basically Im running edgy and have managed to get direct rendering to work with my card but only with a depth of 16; changing the depth to 24 causes direct rendering to stop working. I have search the forums for two days now trying to find a solution and havent found anything really.

Is there a chance that someone can point me in the right direction?

Thanks!

---

### Post by spoon13 on 2006-10-25
Bump! Has anyone else had this problem with other radeon cards not supported by the fglx drivers?

---

### Post by spoon13 on 2006-10-30
Last attempt with a bump on this one... would be nice to get some sort of response since I imagine out of all the ubuntuforums lurkers at least one must be running their 7500 mobility at 24 depth with DRI on.

---

### Post by thm on 2006-11-01
Hi spoon13, I have installed edgy last week and my 7500 Mobility (32MB) is working, as far as I can tell, with DRI at depth 24. Default installation, no tweaks.

As a side note, however, while fiddling with AIGLX and Compiz, I found that depth 24 is too much (i.e. too slow).  Depth 16 feels more responsive.  But depth 24 definitely works here.

What does your Xorg log say?

---

### Post by spoon13 on 2006-11-03
Hey, thanks for responding! I will post up my xorg log when I get home to my laptop. The best so far Ive gotten outta mine is 16 depth with AIGLX and Beryl. Hopefully with help I can figure out why direct rendering turns off at any depth beyond 16.

Thanks!

---

### Post by esaym on 2006-11-03
You need atleast 32mb vid mem to run at 24bit depending on the screen resolution

---

### Post by spoon13 on 2006-11-03
Well shoot, thats disappointing. My IBM T30 only has 16; oh well, thanks for letting me know esaym!

---

### Post by dalem on 2006-11-03
Bought a Pentium 2g. IBM thinkpad t30 with 256K memory, 40g hd, and its nice. But... 

I'm having an awful time getting any sort of accleration going.. I've fought with this for two days and thought I had it figured out yesterday by simply doing a > sudo dpkg-reconfigure xserver-xorg and answering the questions. I selected 24 bit color and later when I did a [glxgears] command, the gears were moving pretty well. Not extremely fast, but pretty well (I don't know how to clock them). I was jazzed!!

Later, I wanted to see if I could get a little better performance, so I rebuilt the kernel with the latest version from kernel.org and somewhere in-between hosed my accleration.

NOw I can't seem to get it working. I've tried reverting to the old kernel, and its the same problem. Here's the output of glxgears:dale@ubuntu:~$ > glxgears
X connection to :0.0 broken (explicit kill or server shutdown)

Does anyone know of a good tutorial to get this set up right?

thanks!

---

### Post by dalem on 2006-11-03
(Sorry for the double posting -- forgot to subscribe to the thread)..

ought a Pentium 2g. IBM thinkpad t30 with 256K memory, 40g hd, and its nice. But... 

I'm having an awful time getting any sort of accleration going.. I've fought with this for two days and thought I had it figured out yesterday by simply doing a > sudo dpkg-reconfigure xserver-xorg and answering the questions. I selected 24 bit color and later when I did a [glxgears] command, the gears were moving pretty well. Not extremely fast, but pretty well (I don't know how to clock them). I was jazzed!!

Later, I wanted to see if I could get a little better performance, so I rebuilt the kernel with the latest version from kernel.org and somewhere in-between hosed my accleration.

NOw I can't seem to get it working. I've tried reverting to the old kernel, and its the same problem. Here's the output of glxgears:dale@ubuntu:~$ > glxgears
X connection to :0.0 broken (explicit kill or server shutdown)

Does anyone know of a good tutorial to get this set up right?

thanks!

---

### Post by 23meg on 2006-11-04
I had this chip in my old laptop, and it's been a long time since I've last tried using it with Ubuntu; could someone posting to this thread confirm that they're actually using Beryl with xorg 7.1 using the default open source ATI driver that comes with xorg and not the proprietary one?

---

### Post by didobuntu on 2006-11-04
> **spoon13 said:**
> Well shoot, thats disappointing. My IBM T30 only has 16; oh well, thanks for letting me know esaym!

Hello Spoon,

supposing that you run ubuntu Edgy, here is my xorg.conf file. My older laptop is an Asus with ATI Mobility Radeon 7500 (32Mb). Direct rendering is OK and Berly/Aiglx run like a charm (but need to be optimized since it is a little slow :mrgreen:).

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"dbe"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
	Option		"AGPMode"	"4"
	Option		"AGPFastWrite"	"true"
	Option		"EnablePageFlip"	"true"
	Option		"DRI"  "true"
	Option		"XAANoOffscreenPixmaps"
	Option		"AccelMethod"  "EXA"
	Option		"ColorTiling"  "on"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option  "AIGLX"  "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option  "Composite"  "Enable"
EndSection



If you are not under Edgy, Delete the last Extensions section since Composite is present only since Egdy Eft.

Good luck

---

### Post by esaym on 2006-11-04
> **spoon13 said:**
> Well shoot, thats disappointing. My IBM T30 only has 16; oh well, thanks for letting me know esaym!
That is just the experience I have had with my ati m6 ( the model before the 7500).  I could run dri at 1400x1050x16 but not 1400x1050x24.  At 24 I would get some buffer error in the logs which according to what I read, was due to lack of video ram.

---

### Post by thm on 2006-11-05
> **esaym said:**
> You need atleast 32mb vid mem to run at 24bit depending on the screen resolution

Is there a page somewhere where those requirements are listed, especially with AIGLX+compiz/beryl?  Even when I run 16bit on my Radeon 7500 32MB, things are not really smooth.  Especially Firefox scrolls remarkably slower (compared to a plain Metacity setup).  Compiz's animations are only supersmooth when I have one or two gnome-terminals open.  As soon as I start firefox, things start to get jerky.  Then again, I have 1600x1200 which might a bit too much for this old Radeon.  But this is my native notebook resolution.

I'd just like to know whether there is anything I can do to improve performance or whether my hardware just isn't able to handle 1600x1200 smoothly.

However, I had to tweak my xorg.conf a bit.  Otherwise 1600x1200 did not work.

Section "Device"
 [...]
 Option "XAANoOffscreenPixmaps" "true"
 Option "GARTSize"              "64"
 Option "EnablePageFlip"        "1"
 Option "ColorTiling"           "1"
 Option "AGPMode" "4"
 Option "AGPFastWrite" "on"
 Option "DynamicClocks" "on"
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

I think only the GARTSize was really necessary (otherwise, my screen was partly corrupted).  I inserted the rest because I found that while blowing away a whole day googling for a good setup and those lines sounded reasonable.

---

### Post by thm on 2006-11-05
> **23meg said:**
> could someone posting to this thread confirm that they're actually using Beryl with xorg 7.1 using the default open source ATI driver that comes with xorg and not the proprietary one?

I am using the open source ati driver, not fglrx (from my xorg.conf: Driver "ati").  With compiz instead of beryl, but well.

---

### Post by sammydee on 2007-02-13
I have a T30 with this video card and 16mb of ram. DRI works just fine on either 16bit or 24 bit colour. However, 24bit colour is a little slow and takes a fair chunk of cpu with Beryl running. 16bit is lightening fast tho. Here is my XORG.conf:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#m
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"dbe"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option  "XAANoOffscreenPixmaps"
	Option      "AGPSize" "32"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection



---

### Post by sammydee on 2007-02-13
oops just noticed, sorry about the thread revival!

---

### Post by kikke on 2008-01-15
Radeon 7500 Mobility is unacceptable slow with opensource ati driver in 24 bit mode. Scrolling a page in firefox is like agony.

---

