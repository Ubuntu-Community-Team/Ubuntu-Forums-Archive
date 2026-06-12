---
title: "Configuration for using built-in Synaptics touchpad with  &quot;SHMConfig&quot; &quot;on&quot; and extern"
date: 2008-12-18
forum: Hardware
---

### Post by brucehobson on 2008-12-18
Guys,

I finally found the secret for using both my built-in Synaptics touchpad with  "SHMConfig" "on" (Shared Memory) and at the same time using a external USB Microsoft Basic Optical Mouse. When I'm portable (On the run) I still have the Synaptics touchpad working without the external mouse. And the best part is I don't have to keep changing/editing my xorg.conf when I'm out and about.

 I'm using a HP-DV9225us Laptop with Ubuntu 8.10.

This has taken many, many months for me to figure out. I guess I'm a bit slow...

Here is a copy of my xorg.conf:


Section "Monitor"
	Option       "CalcAlgorithm" "XServerPool"
	DisplaySize  367 230
	HorizSync    30-70
	Identifier   "Monitor[0]"
	ModelName    "AUO LCD MONITOR"
	Option       "DPMS"
	Option       "PreferredMode" "1440x900"
	VendorName   "Hewlitt Packard Computers"
	VertRefresh  43-60
	UseModes     "Modes[0]"
EndSection

Section "Screen"
	Device       "Device[0]"
	Identifier   "Screen[0]"
	Monitor      "Monitor[0]"
	DefaultDepth	24
	Option         "TwinView" "0"
	Option         "metamodes" "1440x900_60 +0+0; nvidia-auto-select +0+0"
	SubSection     "Display"
        	Depth       24
    		Modes       "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
    Load	   "synaptics"		# Needed by TouchPad
EndSection

Section "DRI"
	Group      "video"
	Mode       0660
EndSection

Section "InputDevice"
	Driver       "kbd"
	Identifier   "Keyboard[0]"
	Option       "Protocol" "Standard"
	Option       "XkbLayout" "us"
	Option       "XkbModel" "microsoftpro"
	Option       "XkbRules" "xfree86"
EndSection

Section "InputDevice"
	Driver       "mouse"
	Identifier   "Mouse[1]"
	Option       "Buttons" "5"
	Option       "Device" "/dev/input/mice"
	Option       "Name" "Microsoft Basic Optical Mouse"
	Option       "Protocol" "explorerps/2"
	Option       "Vendor" "Sysp"
	Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Driver       "synaptics"
	Identifier   "Mouse[3]"
	Option       "Buttons" "5"
	Option       "Device" "/dev/input/mice"
	Option       "Emulate3Buttons" "on"
	Option       "HorizScrollDelta" "0"
	Option       "InputFashion" "Mouse"
	Option       "Name" "Synaptics;Touchpad"
	Option       "Protocol" "explorerps/2"
	Option       "SHMConfig" "on"	# Needed by TouchPad
	Option       "Vendor" "Sysp"
	Option       "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier   "Layout[all]"
	InputDevice  "Keyboard[0]" "CoreKeyboard"
	InputDevice  "Mouse[1]" "CorePointer"
	InputDevice  "Mouse[3]" "SendCoreEvents" # Needed by TouchPad
	Option       "Clone" "off"
	Option       "Xinerama" "off"
	Screen       "Screen[0]"
EndSection

Section "Device"
    BusID		"5:0:0"
    Identifier		"Device[0]"
    Driver		"nvidia"
    VendorName		"nVidia Corporation G70"
    BoardName		"GeForce Go 7600"
    Option		"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option       "AllowMouseOpenFail" "on"
	Option       "ZapWarning" "on"
    	Option 	     "Xinerama" "0"
EndSection

Section "Modes"
	Identifier   "Modes[0]"
EndSection



The secret seems to be in the order in which things are declared...

Hope this helps a few others. Marry Xmas!

Bruce Hobson

---

### Post by brucehobson on 2008-12-18
Guys,

I finally found the secret for using both my built-in Synaptics touchpad with "SHMConfig" "on" (Shared Memory) and at the same time using a external USB Microsoft Basic Optical Mouse. When I'm portable (On the run) I still have the Synaptics touchpad working without the external mouse. And the best part is I don't have to keep changing/editing my xorg.conf when I'm out and about.

I'm using a HP-DV9225us Laptop with Ubuntu 8.10.

This has taken many, many months for me to figure out. I guess I'm a bit slow...

Here is a copy of my xorg.conf:


Section "Monitor"
Option "CalcAlgorithm" "XServerPool"
DisplaySize 367 230
HorizSync 30-70
Identifier "Monitor[0]"
ModelName "AUO LCD MONITOR"
Option "DPMS"
Option "PreferredMode" "1440x900"
VendorName "Hewlitt Packard Computers"
VertRefresh 43-60
UseModes "Modes[0]"
EndSection

Section "Screen"
Device "Device[0]"
Identifier "Screen[0]"
Monitor "Monitor[0]"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "1440x900_60 +0+0; nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection

Section "Module"
Load "dbe"
Load "extmod"
Load "type1"
Load "freetype"
Load "glx"
Load "v4l"
Load "synaptics" # Needed by TouchPad
EndSection

Section "DRI"
Group "video"
Mode 0660
EndSection

Section "InputDevice"
Driver "kbd"
Identifier "Keyboard[0]"
Option "Protocol" "Standard"
Option "XkbLayout" "us"
Option "XkbModel" "microsoftpro"
Option "XkbRules" "xfree86"
EndSection

Section "InputDevice"
Driver "mouse"
Identifier "Mouse[1]"
Option "Buttons" "5"
Option "Device" "/dev/input/mice"
Option "Name" "Microsoft Basic Optical Mouse"
Option "Protocol" "explorerps/2"
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Driver "synaptics"
Identifier "Mouse[3]"
Option "Buttons" "5"
Option "Device" "/dev/input/mice"
Option "Emulate3Buttons" "on"
Option "HorizScrollDelta" "0"
Option "InputFashion" "Mouse"
Option "Name" "Synaptics;Touchpad"
Option "Protocol" "explorerps/2"
Option "SHMConfig" "on" # Needed by TouchPad
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
Identifier "Layout[all]"
InputDevice "Keyboard[0]" "CoreKeyboard"
InputDevice "Mouse[1]" "CorePointer"
InputDevice "Mouse[3]" "SendCoreEvents" # Needed by TouchPad
Option "Clone" "off"
Option "Xinerama" "off"
Screen "Screen[0]"
EndSection

Section "Device"
BusID "5:0:0"
Identifier "Device[0]"
Driver "nvidia"
VendorName "nVidia Corporation G70"
BoardName "GeForce Go 7600"
Option "NoLogo" "True"
EndSection

Section "ServerFlags"
Option "AllowMouseOpenFail" "on"
Option "ZapWarning" "on"
Option "Xinerama" "0"
EndSection

Section "Modes"
Identifier "Modes[0]"
EndSection



The secret seems to be in the order in which things are declared...

Hope this helps a few others. Marry Xmas!

Bruce Hobson

---

