---
title: "[SOLVED] Radeon mobility, how do I get extended screen in Hardy"
date: 2008-08-31
forum: Hardware
---

### Post by rsay on 2008-08-31
I have a radeon mobility on my Dell inspiron 5100 laptop. I occasionally hook up a second monitor when I'm working at my desk. The following xorg.conf worked in 7.10, to give me an extended screen to the right of my laptop monitor, but in 8.04 it gives me a cloned screen. I have tried the graphical configuration tool System>Preferences>Screen Resolution and I can clone or disable the second monitor but I can't get additional workspace.  :confused:

```

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Radeon Mobility 9000 (M7 LW)"
	Driver		"ati"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "true"
        Option          "EnableDepthMoves" "true"
        Option          "EnablePageFlip" "true"
        Option          "DDCMode" "true"
        Option          "Backingstore" "true"
	Option      	"MergedFB"  	"true"
#    	Option      	"MonitorLayout" "LVDS, CRT"
    	Option      	"CRT2Position"  "RightOf"
    	Option      	"CRT2Hsync"     "30-65"
    	Option      	"CRT2VRefresh"  "50-75"
	Option 		"MergedXineramaCRT2IsScreen0" "true"
    	Option      	"MetaModes"     "1400x1050-1024x768"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier   	"External Monitor"
        VendorName   	"Samsung"
        ModelName    	"Syncmaster"
       	HorizSync    	30.0 - 65.0
        VertRefresh  	50.0 - 75.0
      	Option      	"dpms"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon Mobility 9000 (M7 LW)"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"External Screen"
	Device          "Radeon Mobility 9000 (M7 LW)"
        Monitor 	"External Monitor"
      	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Any suggestions are greatly appreciated. My head is starting to get flat from banging into the wall.

---

### Post by rsay on 2008-08-31
I am starting to make progress on this. 
I found the following thinkwiki web page about [XRANDR]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

I started by running dpkg-reconfigure xserver-xorg, said no to using framebuffer and otherwise accepted defaults. I then made the very simple [edits]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf") discussed on the wiki page. This vastly simplified my xorg.conf to the following:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
           Depth		24
           Modes		"1400x1050" "1280x1024" "1024x768"
           Virtual              2424 1050 
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```
**Note the addition of the virtual option under the display subsection. It can be set larger (I tried up to 2800 1050) but this was the largest that would still allow me to have direct rendering.

My Desktop still comes up in clone mode, but now it is at least fixable with xrandr. I used this command to see the current state of my layout (which gave me the identifier of the external monitor as VGA-0.)
```
xrandr -q
```

I can now issue the following commands to get things working:
```
xrandr --output LVDS --auto --output VGA-0 --off
```
```
xrandr --output LVDS --auto --output VGA-0 --mode 1024x768 --left-of LVDS
```

Interestingly if I try to just set it to the left like it was on the previous session nothing happens. (Which is probably why it comes up wrong.) I am now going to try and mess with the startup [script]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login") that they gave to automate the settings on login.

---

### Post by rsay on 2008-08-31
This is now working beautifully. I tried to use the [script]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login") suggested on the thinkwiki in my /etc/X11/Xsessions.d/ but the external screen kept sticking in clone mode. Then I found a post [here]("http://ubuntuforums.org/showthread.php?t=865418") which helped me solve this.

I made the following script, which is slightly but significantly changed, to check if the monitor was connected:

```

#! /bin/sh
## Sets up the desktop based on attachment of external monitor

## Shut off the external monitor
xrandr --output LVDS --auto --output VGA-0 --off

## Turn it back on if it is connected
if xrandr -q |grep -q "VGA-0 connected" ; then
	xrandr --output LVDS --auto --output VGA-0 --mode 1024x768 --left-of LVDS
fi
```

I then put this in my gnome startup programs System>Preferences>Sessions>Startup Programs and things just work.

The key to this working is shutting off the external monitor and then turning it back on in the proper mode if it is connected. For some reason the card balks if you try to go right back to the previous setting and it stays in clone mode. This breaks out of clone mode and gives you a working extended desktop.

---

