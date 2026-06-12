---
title: "Problem switching video cards and getting things working"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by pdnick on 2008-03-15
Well, hello there. I'm really hoping someone can help me out.
I've been having a difficult time getting my video card settings up and running right. I switched from an onboard Radeon 200m graphics card to an NVIDIA GeForce FX 5500 

Intel Celeron D 3.2Ghz 1024Mb RAM (Emachine W3502)

Kernal - 2.6.22-14-generic

lspci -v |grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA])
02:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])

The system BIOS won't let me disable the onboard Radeon card::

more /etc/X11/xorg.conf |grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"


My xorg file as follows::



Section "Files"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"CoreKeyboard"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc104"

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

	Identifier	"NVIDIA GeForce FX 5500"

	Driver		"nvidia"

	BusID		"PCI:2:04:0"

	VideoRam	25600000

	Option		"UseFBDev"		"true"

EndSection



Section "Monitor"

	Identifier	"ADI G66"

	Option		"DPMS"

	HorizSync	30-65

	VertRefresh	50-75

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"NVIDIA GeForce FX 5500"

	Monitor		"ADI G66"

	DefaultDepth	24

	SubSection "Display"

		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

	EndSubSection

EndSection



Section "ServerLayout"

	Identifier	"Default Layout"

	Screen		"Default Screen"

	InputDevice	"Generic Keyboard"

	InputDevice	"Configured Mouse"



# Uncomment if you have a wacom tablet

#	InputDevice     "stylus"	"SendCoreEvents"

#	InputDevice     "cursor"	"SendCoreEvents"

#	InputDevice     "eraser"	"SendCoreEvents"

EndSection

I can't get any desktop effects enabled and it just seems wonky in general.  In “Screens and Graphics” it shows my video card as (NVIDIA GeForce 4 Generic)

Also if I try and change the screen resolution through System>Preferences>Screen Resolution it goes all grey and black and tells me that the configuration failed for whatever setting I'd tried. 

I'm still pretty new to the Ubuntu scene so I've been trying to get around as best as I can. I just figure it's time to ask the experts for help. Anything you say would be much appreciated. 

I'll check back in the AM after I get some sleep. I've been working on this for far too long today. Things are getting better with it, I'd just like everything to work.

---

### Post by pdnick on 2008-03-15
No takers?

---

### Post by taurus on 2008-03-15
If I were you, I would go into the BIOS and turn off the onboard graphic controller.  Then, boot into Ubuntu and if you have a problem with the display, boot into recovery mode from GRUB menu and reconfigure X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Once everything is working again, go into System -> Administration -> Restricted Drivers Manager and enable your nvidia graphic card.  That would install nvidia driver for it.

---

### Post by pdnick on 2008-03-15
> **taurus said:**
> If I were you, I would go into the BIOS and turn off the onboard graphic controller.  Then, boot into Ubuntu and if you have a problem with the display, boot into recovery mode from GRUB menu and reconfigure X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Once everything is working again, go into System -> Administration -> Restricted Drivers Manager and enable your nvidia graphic card.  That would install nvidia driver for it.

Well, I can't disable it through the BIOS, but I can pick and choose which one I'd want. I'll try that again and see where it's at. I've done so many changes I can't remember if I've got it set at the AUTO or the PCI....

---

### Post by pdnick on 2008-03-15
[QUOTE=taurus;4520881
Once everything is working again, go into System -> Administration -> Restricted Drivers Manager and enable your nvidia graphic card.  That would install nvidia driver for it.[/QUOTE]

Well, it seems that all is (kind of) well. There were a couple issues that I should of noticed but I didn't. 

The BIOS was set to AUTO. So I switched to the PCI and then went into the Xorg to fiddle with the settings. It was set to NV instead of NVIDIA, and the RAM it was using was some ridiculously high number. (A few too many zeros) Did a startx and it came to life. Everything's beautiful now.....

However none of the windows seem to have borders so I can't move-resize anything. Not just Firefox, but other programs as well...

EDIT~ Scratch that, I can move the windows via right clicking on the bottom tabs and going to "Move" but there are no window borders or anything to say, grab and resize or move the window.

---

### Post by pdnick on 2008-03-15
> **pdnick said:**
> 

EDIT~ Scratch that, I can move the windows via right clicking on the bottom tabs and going to "Move" but there are no window borders or anything to say, grab and resize or move the window.

Plus the Terminal is now just a white box (Still no borders) with no text or anything in it...

Yes, I'm new to this whole thing and greatly appreciate all the help I can get

---

### Post by pdnick on 2008-03-15
Well, it's got to be an issue with Gnome. I logged out and logged into Kubuntu and everything seems to work great. Everything seems snappier even. I got Compiz to run without a hitch too. So I suppose we'll consider this solved. 

Good ol KDE

---

