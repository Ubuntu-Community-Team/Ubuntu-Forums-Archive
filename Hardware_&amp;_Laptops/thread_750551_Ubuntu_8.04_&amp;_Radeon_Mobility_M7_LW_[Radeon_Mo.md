---
title: "Ubuntu 8.04 &amp; Radeon Mobility M7 LW [Radeon Mobility 7500]"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by wilsonB on 2008-04-09
:(End goal is to get Compiz Beryl up and running..I assume getting the drivers installed and working with gl is first thing to do.:confused:

Someone familiar with this video chipset please post instructions.

I can't even get my notebook graphics drivers to work.
Radeon Mobility M7 LW [Radeon Mobility 7500]
Tried a few things..
I have installed fglrx driver set from package manager. 
I ran; aticonfig --initial
edited my xorg.conf
tried many different additions;
driver="ati", "radeon", "fglrx" '
they are in my driver folder.

It just works with Generic video drivers..

Heres;part of  my xorg.conf

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "radeon"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection


Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection


Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
Option "AIGLX" "true"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection

---

### Post by Rocket2DMn on 2008-04-09
OK, first, your card is definitely not supported for fglrx, it's too old.  You should get rid of fglrx by running
```
sudo apt-get remove --purge xorg-driver-fglrx
```
More here - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and here - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Also, in Hardy, they have been doing a lot of newer things with X which makes it a major pain in the butt to try and configure.  From what I understand, they have dropped support for Compiz Fusion for those of us with the open source "atI"/"radeon" drivers.  There is a rather long and ongoing discussion in this thread about older ATI cards in Hardy - [http://ubuntuforums.org/showthread.php?t=722943](http://ubuntuforums.org/showthread.php?t=722943)
Apparently it is sometimes possible to get CF working by modifying a SKIP_CHECKS in some file somewhere, but I have yet to try it.  However, the chances are that because your card is so old, it isn't likely to work.

Sorry to be the bringer of bad news, but good luck!

---

### Post by ZooLA_IL on 2008-04-24
I'm sorry to bring you the bad news but in Hardy Heron, 
Radeon Mobility M7 LW [Radeon Mobility 7500] HAS BEEN BLACKLIST!

That means that it used to had an open source driver that is not supported in the new distribution of Ubuntu:
> [http://ubuntuforums.org/showthread.php?t=722943](http://ubuntuforums.org/showthread.php?t=722943)
It really sucks because it worked very well in Gutsy Gibbon...
Bug reported:
> [Old Radeon Graphic Cards]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330")

---

### Post by qamelian on 2008-04-24
> **ZooLA_IL said:**
> I'm sorry to bring you the bad news but in Hardy Heron, 
Radeon Mobility M7 LW [Radeon Mobility 7500] HAS BEEN BLACKLIST!

That means that it used to had an open source driver that is not supported in the new distribution of Ubuntu:

It really sucks because it worked very well in Gutsy Gibbon...
The blacklist doesn't mean the card doesn't work. They basically blacklisted a large number of ATI cards because they didn't have time to test each individual variation to see which ones were problematic. My card is also blacklisted, but the SKIP_CHECKS option re-enables the card and it works just fine.

---

### Post by krill on 2008-04-29
I was able to get my Dell Inspiron 5100 (P4 2.4) with the Radeon Mobility 7500 working with Compiz Fusion on 8.04 using the xorg.conf file posted at:
[http://ubuntuforums.org/showthread.php?p=4790762]("http://ubuntuforums.org/showthread.php?p=4790762")[http://ubuntuforums.org/showthread.php?p=4790762](http://ubuntuforums.org/showthread.php?p=4790762)

I use Compiz Fusion Icon to start Compiz. You can install it through apt-get or Synaptic. The package name is "fusion-icon".

```
sudo apt-get install fusion-icon
```

To start Fusion Icon whenever you log in, add it to the Startup Programs list in System-->Preferences-->Sessions.

The cube rotates smoothly for me and many of the desktop effects work great also, including wobbly windows, Expo, etc. **My max resolution is 1024x768, though - if anyone is running this configuration with a higher resolution, please let me know how you acheived it.**

Here's my xorg.conf file, in case it's helpful:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"LVDSBiosNativeMode" "false"
	Option		"GARTSize" "64"
	Option		"AGPSize" "64"
	Option		"AGPMode" "4"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode" "8"
	Option		"AGPFastWrite" "True"
	Option		"EnablePageFlip" "true"
	Option		"EnableDepthMoves" "true"
	Option		"UseInternalAGPGART" "no"
	Option		"BackingStore" "on"
	Option		"UseInternalAGPGART" "no"
	Option		"DMAForXv" "true"
	Option		"AccelMethod" "XAA"
	Option		"ColorTiling" "on"
	Option		"AccelDFS" "true"
	Option		"TripleBuffer" "true"
	Option		"DynamicClocks" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option		"AIGLX" "true"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

