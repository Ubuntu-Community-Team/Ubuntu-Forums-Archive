---
title: "SVIDEO works with Dell e1405 / 640m"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by technomagik on 2007-02-23
its official, it is indeed possible to get your svideo up and running on your dell e1405/640m lappy.

took me weeks to accomplish this xorg file (even tho i just modified someone elses), an its all ya need

back up your original xorg, and use this one. thats all you gotta do. 

no xgl

once you boot into this xorg it'll have your LCD to its native 1200x800 and your svideo at 1024x768, and will allow for 800x600 and 640x480

if you cant get into x with this, start from scratch. i had to

if you get annoyed by the svideo being on all the time follow the instructions on this thread [http://www.ubuntuforums.org/showthread.php?p=2190061](http://www.ubuntuforums.org/showthread.php?p=2190061)

do everything he says but don't use his svideo conf file, you cant get into x with it, and i dont know if his crt clones and extended xorgs work, but his script is genius!! 

remember this only applies to dell e1405/640m lappys, anything else and YMMV


# Workin SVIDEO e1405/640m XORG FILE
# FINALLY!!
# dont work with beryl or any xgl
# I got native 800x1200 for LCD all ready to go just fire up on this xorg
# and it'll load a second desktop to the right of the screen at 1024x768
# dont even bother tryin to get ridda that black border, it's there 
# on 'doze too
# you can do 640x480, 800x600, and 1024x768 if you change depth to 24
# 1024 dies.

# if you cant get in X with this start from fresh install
# tested on Dell e1405/640m with kubuntu and ALL available upgrades

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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO" # "COMPOSITE"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	16

	SubSection "Display"
		Depth	16
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		0 "LCD"
	Screen		1 "TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

---

### Post by technomagik on 2007-02-23
i pasted my xorg and it didnt paste right, sob,  i hate forums. it wouldnt let me upload the txt file either.. if you cant unmangle this email me at  my gmail account livincali ill send you the text file

---

