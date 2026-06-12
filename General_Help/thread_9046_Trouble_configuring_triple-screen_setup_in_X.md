---
title: "Trouble configuring triple-screen setup in X"
date: 2004-12-23
forum: General Help
---

### Post by UnderGod on 2004-12-23
topic says it all, with my current config I have the 2 screens on the TI4200 working properly, but the one on the left (on the tnt2) just mirrors it, don't really understand why :s
anybody that can tell me what I did wrong?
thx

Greetz,
Q

My xconfig
> 
Section "ServerFlags"
      Option       "Xinerama" "true"
EndSection 

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

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
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	BusID		"PCI:2:0:0"
	Driver "nvidia"
	Option "NvAGP" "3"
	Option "DigitalVibrance" "0"
	Option "TransparentIndex" "0"
	Option "CursorShadowAlpha" "64"
	Option "CursorShadowXOffse" "4"
	Option "CursorShadowYOffset" "2"
	Option "Twinview" "TRUE"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" "30-70"
	Option "SecondMonitorVertRefresh" "50-160"
	Option "MetaModes" "1152x864 , 1152x864"
	Option "ConnectedMonitor" "CRT , CRT"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	BusID		"PCI:1:6:0"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"FLATRON 775F"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section	"Monitor"
	Identifier	"left"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"FLATRON 775F"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1152x864"
		EndSubSection
EndSection

Section	"Screen"
	Identifier	"screen1"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"left"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1152x864"
		EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"screen0"
	Screen  1	"screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


thx for your help guys :)

---

### Post by UnderGod on 2004-12-26
*up*
nobody has an idea???
or am I in the wrong section for this kind of questions?
plz help me out here :-/
even an idea of what it could be is welcome :)

Greetz,
Q

---

### Post by varunus on 2004-12-26
One quick thing I noticed:

In the last section, shouldn't it read:

Screen 1 "screen1" LeftOf "screen0"

I'm not sure if X is case-sensitive or not...

Also, does /var/log/XFree86.0.log have any errors about screens or Xinerama in it?

---

### Post by UnderGod on 2005-01-06
problem kinda solved now, though xinerama still doesn't work as it should, fullscreen absolutely wants to spread over 2 screens and movies are stretched as hell (not fun to watch a whole movie like that, so I did a switch to 1/3 screens script ;))

here's my xconfig for those who'd be interested ;)

Greetz,
Q

> 
Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"

    FontPath	"/usr/X11R6/lib/X11/fonts/local/"
    FontPath	"/usr/X11R6/lib/X11/fonts/misc/"
    FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath	"/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath	"/usr/X11R6/lib/X11/fonts/CID/"
    FontPath	"/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/"


#    ModulePath	"/usr/X11R6/lib/modules"

EndSection



Section "Module"



    Load	"dbe"
    Load 	"glx"
    SubSection	"extmod"
#	Option	"omit xfree86-dga"
    EndSubSection

    Load	"type1"
    Load	"freetype"

EndSection



Section "ServerFlags"

#    Option	"NoTrapSignals"
#    Option	"DontVTSwitch"
#    Option	"DontZap"
#    Option	"DontZoom"
#    Option	"DisableVidModeExtension"
#    Option     "AllowNonLocalXvidtune"
#    Option	"DisableModInDev"
#    Option	"AllowNonLocalModInDev"

    Option	"blank time"	"10"	# 10 minutes
    Option	"standby time"	"20"
    Option	"suspend time"	"30"
    Option	"off time"	"60"

# Option   "EstimateSizesAggresively" "0"

EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"keyboard"

#    Option	"Protocol"	"Xqueue"
    Option	"AutoRepeat"	"500 5"
#    Option	"Xleds"	"1 2 3"
#    Option	"XkbDisable"
#    Option	"XkbModel"	"pc102"
#    Option	"XkbModel"	"pc105"
#    Option	"XkbModel"	"microsoft"
#    Option	"XkbModel"	"pc104"
#    Option	"XkbLayout"	"de"
#    Option	"XkbLayout"	"de"
#    Option	"XkbVariant"	"nodeadkeys"
#    Option	"XkbOptions"	"ctrl:swapcaps"



    Option	"XkbRules"	"xfree86"
    Option	"XkbModel"	"pc105"
    Option	"XkbLayout"	"be"
#    Option	"XkbVariant"	""
#    Option	"XkbOptions"	""

EndSection


Section "InputDevice"

    Identifier	"Mouse1"
    Driver	"mouse"
    Option	"Protocol"	"IMPS/2"
    Option	"Device"	"/dev/mouse"
	Option	"ZAxisMapping"	"9 10"
#    Option	"Protocol"	"Auto"
#    Option "Protocol"	"PS/2"
#    Option	"Protocol"	"Xqueue"
#    Option	"BaudRate"	"9600"
#    Option	"SampleRate"	"150"
     Option	"Emulate3Buttons"	"0"
     Option	"Buttons"		"10"
#    Option	"Emulate3Timeout"	"50"
#    Option	"ChordMiddle"

EndSection

Section "Monitor"
    Identifier	"Generic Monitor"
    HorizSync	31.5-82
    VertRefresh	50-100  # typical for a single frequency fixed-sync monitor
EndSection

Section "Monitor"
	Identifier	"left"
	HorizSync	31.5-82
	VertRefresh	50-100
EndSection

Section "Device"

    Identifier	"ti"
    Driver	"nvidia"
   BusID	"PCI:2:00:0"

EndSection

Section "Device"
	Identifier	"tnt"
	Driver		"nvidia"
	BusID		"PCI:1:6:0"
EndSection


Section "Screen"
    Identifier	"Screen 1"
    Device	"ti"
    Monitor	"Generic Monitor"
    DefaultDepth 24
    Subsection "Display"
	 Depth 24
	Modes "1152x864"
	ViewPort 0 0
	Virtual 0 0
EndSubsection	 
	Option	"Twinview"
	Option	"SecondMonitorHorizSync"	"31.5 - 82"
	Option	"SecondMonitorVertRefresh"	"50 - 100"
	Option	"MetaModes"	"1152x864,1152x864"
	Option	"TwinViewOrientation"	"RightOf"
EndSection

Section "Screen"
	Identifier	"Screen 2"
	Device		"tnt"
	Monitor		"left"
	DefaultDepth	24
	Subsection	"Display"
		Depth	24
		Modes 	"1152x864"
		ViewPort	0 0
		Virtual		0 0
	EndSubsection
EndSection

Section "ServerLayout"

    	Identifier	"Main Layout"
    	Screen	"Screen 1"
    	Screen  "Screen 2" LeftOf "Screen 1"
	InputDevice	"Mouse1" "CorePointer"
    	InputDevice "Keyboard1" "CoreKeyboard"
	Option		"Clone"	"off"
	Option		"xinerama"	"on"
EndSection


---

### Post by fng on 2005-01-06
Tripple screen????!!!@!@!? 
Are you mad? :)

---

