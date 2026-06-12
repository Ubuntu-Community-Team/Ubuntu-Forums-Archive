---
title: "tdfx driver crashes gnome in edgy"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by GameboyHippo on 2006-10-23
I've been running Ubuntu Dapper Drake on my PC with a Voodoo 3 3000 PCI video card.  I decided to try out Edgy Eft.  When I updated, I ran into a slight problem.  The Gnome Desktop resets when I log in.

I'll log in with my credentials and as soon as my wallpaper loads, X resets.  With KDE, X resets when I scroll in Konqueror or I try using Firefox.

This strange X resetting problem only occurs if I'm using the tdfx driver.  If I use vesa, the problem is not there, but it significantly impacts my ability to run 3D applications such as screensavers.  I've tried disabling glx and dri for kicks and the issue still persists with the tdfx driver.

Has anyone else run into this issue?  I know it would be easier to just buy a $30 nVidia card, but it's looking like a broke winter.

Anyway, here is my xorg.conf file:

```

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"vesa"
        #Driver          "tdfx"
	BusID		"PCI:0:9:0"
EndSection

Section "Monitor"
	Identifier	"XF-7b"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"XF-7b"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by sygin on 2006-10-29
Hi,

I have to use the vesa driver with mu Voodoo 3 graphics card.
The tdfx driver does not work correctly.

This issue is a problem for me, as the VESA driver barely works.
Hopefully there will be an update to this issue.

Thanks
Sygin

---

### Post by Diskdoc on 2006-10-29
I have the exact same problem running XUbuntu with XFCE. Upgraded from Dapper to Edgy and xorg keeps crashing after eventually letting me log on. Crashes with tdfx, works with vesa. Seems this is a bug that should be fixed.

---

### Post by kingcharles1666 on 2006-10-31
identical problem to gameboyhippo however I could not get vesa to work so I am back at 6.06 :-(

---

### Post by abirdman on 2006-11-04
I have exactly the same problem as the parent poster. vesa driver works. tdfx driver causes gnome to crash when the wallpaper loads. There was originally a problem with 24 bpp color depth which kept gdm from loading at all, but I changed to 16. Now i get gdm, and login normally, but gnome stops at wallpaper, and the gdm comes back up with the login screen.

Any suggestions would be welcome.

---

### Post by mooglie on 2006-11-09
See this thread:

[http://www.ubuntuforums.org/showthread.php?t=292580](http://www.ubuntuforums.org/showthread.php?t=292580)

---

### Post by Joe_CoT on 2006-11-16
*edited* sorry, wrong thread :-/

---

### Post by travm on 2007-03-21
can anyone help me, im new and i have this problem.  How do i recompile my tdfx driver, and how do i apply the patch?  better yet, i followed that link and I cant find the actual patch, where is it?
dying to get hardware display drivers working.

---

### Post by sygin on 2007-04-17
Hi,

I think that the problem is fixed in the new Ubuntu version "Feisty Fawn". 
Upgrading to this version should fix your problem.

Cheers
Sygin.

---

