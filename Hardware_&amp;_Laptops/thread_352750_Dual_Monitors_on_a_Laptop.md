---
title: "Dual Monitors on a Laptop"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by dano2769 on 2007-02-03
I recently installed Ubuntu 6.10, and I'm trying to get dual monitors to work. I copied the idea of an xorg.conf I found online, but it does work. Can anyone help?

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410) 2"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section	"Monitor"
	Identifier	"Samsung Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Samsung Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410) 2"
	Monitor		"Samsung Monitor"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option		"Xinerama" "ON"
EndSection

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen		0 "Laptop Screen" 0 0
	Screen		1 "Samsung Screen" RightOf "Laptop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

---

### Post by RandomJoe on 2007-02-03
Does it do _anything_?  What does /var/log/Xorg.0.log have in it?  This shows a log of everything the X server did the last time it started (or tried to).

Right off, nothing looks particularly wrong other than the 'Option "Xinerama" "ON"' is usually in everything I've seen and done just another line inside the ServerLayout section, not in ServerFlags.  (I don't even have a ServerFlags section.)  It also usually uses "true" instead of "on", but that may be valid as well - not sure how flexible xorg is with boolean descriptors...

Just checking to be thorough - did you use 'lspci' to get that "PCI:1:5:0" BusID for your card?

---

### Post by dano2769 on 2007-02-03
It boots as it would normal. In this case, it only had the external monitor on and not the laptop monitor. If I unplug the external monitor, it works like normal.

Xorg.0.log has these lines of interest:
```
(WW) RADEON(0): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
Please use the radeon MergedFB option if you want Dual-head with DRI.
```
#This obviously seems to be the solution, but I don't know what DRI is and whether or not I need to be running it.
```
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
```
```
(WW) RADEON(1): Only one monitor detected, Second screen will NOT be created
```


I'll try changing xinerama to "true" instead, and the BusID was the default in Xorg.

---

### Post by dano2769 on 2007-02-03
Okay, I have both monitors working using the code below. But the new problem is that both monitors have to be on the same resolution. Is there a way to have the monitors using different resolutions? As it is, changing either of the MetaModes does not fix it because one monitor will stop working then.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option "MergedFB" "true"
 	Option "MonitorLayout" "LVDS, CRT"
	Option	"CRT2Position" "RightOf"
	Option	"MetaModes"	"1280x800-1280x800"
 	Option "CRT2Hsync" "30-81" 
 	Option "CRT2VRefresh" "60-75"
EndSection
```

---

### Post by Sparken on 2007-12-09
I got this working on my HP/Compaq nx9010 Laptop and a Samsung SyncMaster LCD display.
The laptop has a video card that Ubuntu Feisty is seeing as an ATI Radeon IGP 340M.
I am using the stock ATI drivers that Ubuntu came with, have downloaded no extra stuff.

It was frustrating, very frustrating getting this to work the way I am accustomed so I am
posting it here in case it may help someone else. 

This setup allows the laptop screen to be recognized as the primary monitor (taskbar,etc there
by default) and the Samsung LCD to work beside it. Windows will maximize to either screen
individually, not maximize to fill both monitors. Windows, icons, etc can be dragged from
one monitor to the other or anywhere in between. The monitor resolutions can be set to
different sizes (ie 1040x768 on one 1240x1028 on the other) none of the desktops will scroll
around on a monitor, they are full screen, fixed, like normal.

One flaw I found is that since Xinerama needs to be set "true", it causes the python 
based powermanager application to crash on login and also the Ubuntu "System Settings"
control panel application will crash when you click on "Monitor & Display". This goes 
away when Xinerama is turned off, so you may want to switch between 2 configs a single
monitor config for on the go and double for home/office.

**Preperation:**
Backup your old config! Be prepared to restore it from the 
recovery console if X and KDM will not run. You may also need
to borrow settings from it.

You will need to set at least 32MBs for the AGP memory set in the laptop Bios.
Less memory can cause some weirdness and drag system to a halt upon
opening windows.

**Here is the Xorg.conf which is all I had to change:**

*[COLOR="DimGray"]-- I left out the top of the config which sets up pointing devices --[/COLOR]*
==========================================
Section "Device" *[COLOR="DimGray"]# First Video Port - used for Laptop Intenal Screen[/COLOR]*
  identifier "ATI Technologies Inc Radeon IGP 330M/340M/350M (Primary)"
  boardname "ati"
  busid "PCI:1:5:0" *[COLOR="DimGray"]# This is from my stock config - use whatever yours says[/COLOR]*
  driver "ati"
  Option "MonitorLayout" "LVDS, CRT" [I][COLOR="DimGray"]# this order is critical - don't modify it 
                                                     # "CRT" has nothing to do with the actual hardware
                                                     # - just go with the flow here[/COLOR][/I]
  Option	"MetaModes"	"1024x768-1280x1024"  [I][COLOR="DimGray"]# two screen resolutions you want
                                                                             # laptop resolution is set first, 
                                                                             # regardless of position[/COLOR][/I]
  screen 0
  option "MergedFB" "off" [I][COLOR="DimGray"]# Yes leave off if you want to be able to move items 
                                    # between windows and are using Xinerama[/COLOR][/I]
EndSection
Section "Device" *[COLOR="DimGray"]# Second Video Port - used for External device on VGA connector[/COLOR]*
  identifier "ATI Technologies Inc Radeon IGP 330M/340M/350M (Secondary)"
  boardname "ati"
  busid "PCI:1:5:0" *[COLOR="DimGray"]# Same as the first video device[/COLOR]*
  driver "ati"
  screen 1
  option "MergedFB" "off" [I][COLOR="DimGray"]# Yes leave off if you want to be able to move items 
                                    # between windows and are using Xinerama[/COLOR][/I]
EndSection



Section "Monitor" 
  identifier "Laptop LCD"
  vendorname "Generic"
  modelname "Flat Panel 1024x768"
  HorizSync 31.5-55
  VertRefresh 40-70
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
*[COLOR="DimGray"]# I chopped off the modelines I didn't want the laptop to use (ie 800x600  )[/COLOR]*
gamma 1.0
EndSection


Section "Monitor" 
  identifier "External Monitor"
  vendorname "Plug 'n' Play"
  modelname "Samsung SyncMaster"
  HorizSync 30.0 - 81.0
  VertRefresh 56.0 - 75.0
option "DPMS"
[I][COLOR="DimGray"]# This lets the system probe my LCD for modes, 
# I still needed the correct Sync & refresh rates 
# manually to get the monitor to display clearly.
# You may need to tweak the Hor And Vert to get
# Your display to work properly[/COLOR][/I]
EndSection



Section "Screen" *[COLOR="DimGray"]# this is the laptop display[/COLOR]*
  Identifier "Internal Screen"
  Device "ATI Technologies Inc Radeon IGP 330M/340M/350M (Primary)"
  Monitor "Laptop LCD"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@75" "1024x768@70" "1024x768@60" *[COLOR="DimGray"]#Modes I will allow[/COLOR]*
  EndSubSection
EndSection

Section "Screen" *[COLOR="DimGray"]# this is the external monitor[/COLOR]*
  Identifier "External Screen"
  Device "ATI Technologies Inc Radeon IGP 330M/340M/350M (Secondary)"
  Monitor "External Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024" *[COLOR="DimGray"]#Modes I will allow[/COLOR]*
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Internal Screen" 0 0
  screen 1 "External Screen" rightof "Internal Screen" [I][COLOR="DimGray"]# Sets the position 
                                                                             # in relation to the laptop screen[/COLOR][/I]
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666 *[COLOR="DimGray"]# Number of the beast - How appropriate[/COLOR]* 
EndSection

Section "ServerFlags"
  option "Xinerama" "true" *[COLOR="DimGray"]# Allows you to drag items between screens[/COLOR]*
EndSection

=============================================

---

