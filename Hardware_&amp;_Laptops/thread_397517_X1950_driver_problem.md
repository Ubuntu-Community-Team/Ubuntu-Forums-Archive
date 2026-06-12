---
title: "X1950 driver problem"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by jimtb on 2007-03-30
Yesterday I bought a new VGA, Saphire X1950 Pro on AGP bus. 

I spent several hours trying to get it work right under ubuntu, I had to go back to xorg 7.1 and kernel 2.6.19 and I finally managed to install the drivers and the module following the unofficial ATI driver wiki.

However, when I log into X server, there are many many problems...The screenshot will help you understand what I mean. The only temporary solution I have found is to enable compositing so I can use mesa instead of fglrx and have 2D acceleration, but this worse than it seems, as it is difficult to watch full screen movies for example.

This is the output of fglrxinfo right now:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

Everything seems normal when I have composite disabled, direct rendering is enabled, but everything becomes corrupted as soon as I move a Window or scroll down a page in firefox.

Also here's my xorg.conf 
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/usr/local/myTTF"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us,gr"
	Option	    "XkbOptions" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
	Option	    "XkbVariant" ",nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"

#	Option	    "Centermode" "off"
	Identifier  "ATI RADEON X1950Pro"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X1950Pro"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

##Section "Extensions"
##        Option      "Composite" "0"
##EndSection
```

Is there anything I can do to fix this?

---

### Post by jimtb on 2007-03-31
For the record, the only thing I had to do to get rid of this problem was to change the AGP Aperture size in my BIOS from 128 to 256MB.

---

### Post by 00arthuryu on 2007-04-17
you have to disable the composite as they don't work with X1950 ati cards, get rid of the # on the composite in your xorg.conf

---

### Post by itsjustarumour on 2007-04-28
I have exactly the same problem with this card.  I've already disabled composite, and I don't have an option in my BIOS to change the AGP Aperture size from 128 to 256MB.  The latest Envy installs the driver but there is still no 3D acceleration, and I've tried a manual install of the driver downloaded from the ATI site but got exactly the same result as with Envy...

---

### Post by 00arthuryu on 2007-05-08
you have conflicting drivers, from what i know, envy doesn't work with ati drivers
the method 2 of the ati unoffical wiki works as method 1 has very old drivers, you need to uninstall envy before hand though

---

### Post by itsjustarumour on 2007-05-08
> **00arthuryu said:**
> you have conflicting drivers, from what i know, envy doesn't work with ati drivers
the method 2 of the ati unoffical wiki works as method 1 has very old drivers, you need to uninstall envy before hand though

Hi Arthuryu
Thanks for the post, but I've already tried that!  I've experimented with numerous fresh installs, with and without Envy, each of the drivers, and official/unofficial howtos.  Still no joy.  And while I've been at it, I've experienced a host of other niggling issues with ATI that I won't go into here.  I've spent literally days on this and can't do without it any longer.  So as of 2 days ago, and with the very greatest regret (and feeling just a little bit cheesed off with Ubuntu), heres my solution to the problem:  :-(  

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ih=012&sspagename=STRK%3AMESE%3AIT&viewitem=&item=220109620364&rd=1&rd=1](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ih=012&sspagename=STRK%3AMESE%3AIT&viewitem=&item=220109620364&rd=1&rd=1)

Thanks again fror trying to help anyway  :-D

---

