---
title: "Switch from Dual monitor to single without restarting gdm?"
date: 2008-10-31
forum: General Help
---

### Post by sdlyr8 on 2008-10-31
I have my work laptop running ubuntu 8.04 and have a 20inch monitor hooked up to it, but when i leave to go home I do not have that extra 20 inches. I currently just have 2 xorg files and i'll switch them out and restart gdm when I do the switch. However that causes me to have to close all windows and reopen them which is a big pain in the ***. Is there a way to switch without losing all my data?

Thanks in advance!

---

### Post by PsychedelicReaction on 2008-10-31
if you have an nvidia card, nvidia-settings has an easy way to do it. but i don't know about other cards...

---

### Post by MartinSz on 2008-11-10
Hi, 

I have a similar problem. From what I've read, it might be possible to switch between monitor modes by setting up the admissible resolutions in xorg.conf, so that you have both resolutions for single and dual monitor and then use "Crtl-Alt-+" to cycle between them w/o restarting gdm. 
On the downside, I have no idea how exactly this should work. Here's my xorg.conf for 2 monitors:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "DesktopSetup"  "horizontal,reverse" #Enable Big Desktop
	Option "Mode2"         "1680x1050" #Resolution for second monitor
	Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
	Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Any idea how to set it up so I could switch through the right resolution modes?

Thanks!
Martin

---

