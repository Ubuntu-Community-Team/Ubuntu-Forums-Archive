---
title: "Fn &amp; screen on T42P"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by walrus_t on 2006-10-30
First sorry for my bad english, i'll try to clearly explain my problem.
I've just installed Edgy on my T42P (fresh install) and i've got this problem: when my laptop "wakes up" from screensaver (i use blank screensaver) what appears when i try to change contrast appears for one second, and then disappears. It's not really a problem but, when i watch some video with totem, and try to change volume then, what appears when i try to change volume shows, then disappears leaving a black rectangle where it has appeared.
Can someone help me please?

P.S.: sorry again for this bad bad english ](*,)

---

### Post by rbalfour on 2006-10-30
Post the output from lspci  and the contents of /etc/X11/xorg.conf

---

### Post by walrus_t on 2006-10-30
lspci gives me:

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

and here is my xorg.conf:

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
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
	Option    	"EmulateWheel"          "true"
        Option    	"EmulateWheelButton"    "2"
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
	Identifier	"ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
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
	Mode	0666
EndSection

```

Thanks!

---

### Post by rbalfour on 2006-10-31
In your xorg.conf

Change the following:

> 
Section "Device"
	Identifier	"ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection


to

> 
Section "Device"
	Identifier	"ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
	Option "AGPFastWrite" "on"
EndSection


See if that will clear up the issue.

---

### Post by walrus_t on 2006-10-31
It didn't clear the issue :(
I tried changed my xorg.conf but when i uncomment the line "Option AGP Mode", X server just doesn't boot. (whether x was 2 or 4): i had to use recovery mode to revert the changes.
With the modifications and with the line "Option AGP Mode" left commented, it doesn't clear the issue. :(

---

### Post by walrus_t on 2006-10-31
It didn't clear the issue :(
I tried changed my xorg.conf but when i uncomment the line "Option AGP Mode", X server just doesn't boot. (whether x was 2 or 4): i had to use recovery mode to revert the changes.
With the modifications and with the line "Option AGP Mode" left commented, it doesn't clear the issue. :(

---

### Post by rbalfour on 2006-10-31
Can you post a screenshot of the issue in action?

---

### Post by walrus_t on 2006-11-01
Sure, here are two screenshots of my totem player:

[http://dcaisson.free.fr/issue](http://dcaisson.free.fr/issue)

You cannot see the movie behind but i guess it's not important. Here is what happens: i play a movie and when i press volume keys i get the first picture (sound_settings_appears.jpg) then, sound settings disappears and i get what's on the second picture (leaving_a_black_rectangle_after.jpg).
That happens only when i watch a movie in fullscreen mode.
And it doesn't happens if, for example, i watch some photos (with gThumb) in fullscreen mode and try to change contrast or volume: no black rectangle is left after that and everything's fine.

---

