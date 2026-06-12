---
title: "Some synaptics touchpad options in xorg.conf are ignored!?"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by maddoxflower on 2007-11-02
I am encountering a very strange behaviour with my xorg.conf settings concerning my synaptics touchpad. Some options are ignored while others take effect properly. E.g. my settings for 'RBCornerButton' are correctly configured but my settings for 'FingerLow' and 'FingerHigh' are ignored. Changing values via ```
synclient option=value
``` works fine. This is on a Samsung X20 1730 V laptop running a more or less fresh Gutsy, by the way. Any suggestions?

Here's my xorg.conf:
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"SHMConfig"		"on"
	Option		"Emulate3Buttons"	"on"
EndSection

Section "InputDevice"
# see 'man synaptics' for explanations of options
# to see the output of touchpad actions, type 'synclient -m 1'; to list
# current settings, type 'synclient -l'
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
	Option		"HorizEdgeScroll"	"0"
	Option 		"LeftEdge"		"0"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"0"
	Option		"BottomEdge"		"4100"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"2"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

And this is the output of ```
synclient -l
``` after restarting X:
```
Parameter settings:
    LeftEdge             = 0
    RightEdge            = 5300
    TopEdge              = 0
    BottomEdge           = 4100
    FingerLow            = 10
    FingerHigh           = 15
    MaxTapTime           = 180
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 60
    HorizScrollDelta     = 80
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 0
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.0822368
    MaxSpeed             = 0.197368
    AccelFactor          = 0.00164474
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 304
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 0
    RBCornerButton       = 2
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0.01
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
```

---

### Post by defaulk on 2007-11-26
Sorry, I don't have an answer but I do have the same problem.  Some settings in xorg.conf don't seem to take, but entering them using synclient does work.  Why might this be?

---

