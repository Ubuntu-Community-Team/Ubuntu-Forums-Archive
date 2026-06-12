---
title: "external monitor setup using mergedfb"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by aerials on 2005-04-16
I'm running Hoary on a Thinkpad T42 and everything works just fine, including suspend to disk, as long as I don't install fglrx ;)

I now tried to get the external monitor to work in a way I can use it. I only need it for presentations, but because those beamers only support resolutions between 1024x768 and 1280x1024 I can't just clone my 1400x1050 screen.

After a few research I found a possible solution using the mergedfb and changed my xorg.conf according to the instructions I found here: [http://www.botchco.com/alex/radeon/mergedfb/cvs/DRI/final/radeon.4.html](http://www.botchco.com/alex/radeon/mergedfb/cvs/DRI/final/radeon.4.html)

Now I can connect my 15inch XGA LCD screen and have my Gnome desktop split over the 2 screens. But the my problem is now, that the desktop stays split even after I disconnect the external LCD or boot without connecting it. Is there an option that the driver autodetects if a screen is connected?

My xorg.conf looks like this (hope this thing isn't too messed up):

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbOptions"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"ati"
	Option		"MergedFB"		"true"
	Option		"CRT2Position"		"RightOf"
	Option		"CRT2Hsync"		"31.5-60"
	Option		"CRT2VRefresh"		"56-75"
#	Option		"MergedXineramaCRT2IsScreen0"	"false"
	Option		"MetaModes"		"1400x1050-1024x768 1024x768"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
       	HorizSync	31.5 - 60
        VertRefresh	56 - 75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"External Screen"
	Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
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

Has anybody else successfully realised a setup like that? Thanks in advance for any hints. :)

---

### Post by sarimak on 2006-04-26
The same problem. If I connect external LCD to notebook (HP compaq nc6000) before startx the screen spreads on both monitors. If I disconnect external LCD the half of screen is unavailable. If I hibernate (no matter if with or without external LCD connected) and resume without external LCD the half of screen is unavailable too. The only way to get usual 1400x1050 resolution is to exit from X and start it again without external LCD connected.

Then (without external LCD) if I try to use XRandR via resapplet to change resolution from 1400x1050 to 2680x1050 it applies only to primary LCD and I'm only able to scroll left and right with the viewport of virtually double-sized screen and no way to get external LCD to work. In addition the external LCD shows "no signal" on VGA.

xserver-xorg   7.0.0-0ubuntu2
VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
recent kernel 2.6.15-21-686 on DapperDrake preview


My Xorg config:

```
sarim:~$ cat /etc/X11/xorg.conf | grep -v \#
Section "Files"
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "xtrap"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "synaptics"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "Device"        "/dev/input/mouse1"
    Option      "Protocol"      "auto-dev"
    Option      "Emulate3Buttons"
    Option      "ZAxisMapping"  "4 5"
    Option      "SHMConfig"     "true"

    Option      "LeftEdge"      "1700"
    Option      "RightEdge"     "5300"
    Option      "TopEdge"       "1700"
    Option      "BottomEdge"    "4200"
    Option      "FingerLow"     "25"
    Option      "FingerHigh"    "30"
    Option      "MaxTapTime"    "180"
    Option      "MaxTapMove"    "220"
    Option      "VertScrollDelta" "100"
    Option      "MinSpeed"      "0.12"
    Option      "MaxSpeed"      "0.24"
    Option      "AccelFactor" "0.0020"
    Option      "UpDownScrolling" "true"
    Option      "CircularScrolling" "true"
    Option      "CircScrollTrigger" "0"
    Option      "ClickTime"     "100"
EndSection

Section "InputDevice"
    Identifier  "USB Mouse"
    Driver      "mouse"
    Option      "Device"         "/dev/input/mice"
    Option      "Device"         "/dev/input/mouse0"
    Option      "Protocol"       "auto"
    Option      "ZAxisMapping"    "4 5"
EndSection

Section "Device"
        Identifier      "Radeon Mobility 9600 MergedFB"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "MergedFB"      "true"
        Option          "CRT2HSsync"    "31.5 - 60.0"
        Option          "CRT2VRefresh"  "60-85"
        Option          "MonitorLayout" "LCD,CRT"
        Option          "OverlayOnCRT2" "true"
        Option          "MetaModes"     "1400x1050-1280x1024"
        Option          "CRT2Position"  "RightOf"
EndSection

Section "Monitor"
        Identifier      "Generic LCD"
        Option          "DPMS"
        Option          "DDCMode" "on"
EndSection

Section "Screen"
        Identifier      "MergedFB Screen"
        Device          "Radeon Mobility 9600 MergedFB"
        Monitor         "Generic LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
                Virtual         2680 1050
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "MergedFB Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Synaptics Touchpad" "AlwaysCore"
        InputDevice     "USB Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

