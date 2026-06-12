---
title: "button and tap-to-click don't work on touchpad"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by linuxguiri on 2006-11-07
The left/right buttons AND the tap-to-click on my Synaptics touchpad always STOP working within a few minutes of starting Ubuntu. ](*,)

I have only found two ways to get them working again:
* Reboot X (via CTRL-ALT-BACKSPACE).
* Or if I have a window open (i.e. terminal, etc) I can ALT-TAB between windows and the touchpad buttons and tap-to-click eventually work again. However, they will stop working again within a few minutes and I will have to repeat.

Anyone had similar problems or have some ideas to try?

(It' s near impossible to use Gnome GUI without a functioning mouse/touchpad.)

ALREADY TRIED:
* installed gsynaptics
* adjusted touchpad settings via
* added [Option "SHMConfig" "on"] to xorg.conf
* touchpad functions perfectly in WinXP

SYSTEM INFO:
Inspiron 9400 (Brand new)
Core 2 Duo T5600 (Intel 64)
Synaptics TouchPad
NVIDIA GeForce 7900 256MB
Edgy Eft x86_64 (FRESH INSTALL on brand NEW computer)

/etc/X11/xorg.conf:
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
#	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"intl"
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
	Option		"SHMConfig"		"on"
EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

Section "Device"
	Identifier	"256 MB NVIDIA GeForce Go 7900 GS"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP"		"1"
EndSection

Section "Monitor"
	Identifier	"Dell UltraSharp 17 inch Wide Screen UXGA with TrueLife"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"256 MB NVIDIA GeForce Go 7900 GS"
	Monitor		"Dell UltraSharp 17 inch Wide Screen UXGA with TrueLife"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
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
	InputDevice	"Synaptics Touchpad" #"AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by linuxguiri on 2006-11-10
Solved by adding "notsc" to kernel options.

More info here:
[http://ubuntuforums.org/showthread.php?t=296354](http://ubuntuforums.org/showthread.php?t=296354)

---

