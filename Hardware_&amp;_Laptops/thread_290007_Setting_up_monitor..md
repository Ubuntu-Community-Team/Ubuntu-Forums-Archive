---
title: "Setting up monitor."
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by one4house on 2006-10-31
I have recently switched from Kubuntu to Ubuntu. I Kubuntu I had to enter the Maker and model of my monitor to get a full list of screen resolutions. I cannot seem to find anywhere to enter this information in Ubuntu. Can someone point me in the right direction? I already know about the /etc/X11/xcon.conf file. But in this file it still list my monitor as GENERIC so it does not give me a full list of screen resolutions to chose from.

---

### Post by happy-and-lost on 2006-10-31
System-->Preferences-->Screen Resolution may be a good place to start.

If your problem isn't solved there, post the contents of your /etc/X11/xorg.conf file.

---

### Post by one4house on 2006-10-31
Double post

---

### Post by one4house on 2006-10-31
> **happy-and-lost said:**
> System-->Preferences-->Screen Resolution may be a good place to start.

If your problem isn't solved there, post the contents of your /etc/X11/xorg.conf file.
  

I did start in the SYSTEM>PREF.>SCREEN RESOLUTION and there is nowhere to enter make or model on my monitor. In Kubuntu there was another drop-down menu for entering this information.

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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

[B]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection[/B]

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x854" "1152x768" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x854" "1152x768" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x854" "1152x768" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x854" "1152x768" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x854" "1152x768" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x854" "1152x768" "1024x768" 
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by happy-and-lost on 2006-10-31
What is it you actually want to do? You want a res higher than 1152x768?

---

### Post by one4house on 2006-10-31
Forgot to mention: in my drop down menu, in the SCREEN RESOLUTION settings, I do not even have the 1280 x 854 as an option even though it is listed in the xcon.conf file. I think this stems from the fact that it sees my monitor as GENERIC. ](*,)

---

### Post by one4house on 2006-10-31
Yes, either higher resolutions or icons that are not 10% of the screen at 1024 x 768.

---

### Post by stream303 on 2006-10-31
Here's a quick way to get to the open-source nv driver:

```
 sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
```

This brings up a friendlyl gnome dialog and allows you to select your driver and the resolution.  Much better than default for sure!

---

### Post by one4house on 2006-11-01
Is there any way to get the driver from Kubuntu loaded into Ubuntu? I know that all I need to do is set it to where my monitor is recognized as a Viewsonic e70 instead of GENERIC MONITOR(see bold print in xcon.conf)and then I will be able to set it to the resolution to what I want. I just do noit know how to do this.

---

