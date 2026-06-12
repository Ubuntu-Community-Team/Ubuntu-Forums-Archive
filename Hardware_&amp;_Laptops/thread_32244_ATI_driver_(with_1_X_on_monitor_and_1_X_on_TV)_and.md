---
title: "ATI driver (with 1 X on monitor and 1 X on TV) and xv extension"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by cyberlab on 2005-05-06
So i have 2 X independant session (TV and Monitor)
It's **OK** for all DIVX with the openGL driver on monitor or TV with a CPU overload
It's **OK** for all DIVX with the xv extension on monitor
It's **KO** for playing DIVX with the xv extension on TV

I summarize

- driver fgrlx are installed and fonctionnal (fglrx-control + xorg-driver-fglrx). **OK**
- test with glxgears and fgl_glxgears. **OK**
- configuration of one X session on CRT monitor (1152x864 - 75 Hz). **OK**
- configuration of second independant X session on TV (800x600 - 60 Hz). **OK**
- fullscreen DIVX playing on monitor with mplayer -vo gl (or gl2). **OK** (but CPU overload, some DIVX even not playing without lag)
- fullscreen DIVX playing on monitor with mplayer -vo xv. **OK** (all divx)
- fullscreen DIVX playing on TV with export DISPLAY=:0.1 + mplayer -vo gl (or gl2). **OK **(but CPU overload)
- fullscreen DIVX playing on TV with export DISPLAY=:0.1 + mplayer -vo xv. **KO the problem is here.**

When i'm export display for playing DIVX on TV with the xv extension, *(there are horible green band which blink horizontally on the TV screen)**, there are some bug on the screen of my monitor (big green rectangular cursor and green band blinking horizontally at the bottom of the screen)

[img]http://taltan.free.fr/bug.png[/img]

** The green band on TV are disappear with this new xorg.conf* 

So if someone had idea, i'll take it !!

Here my configuration

```

--------------
Hard
--------------
PIII 900
512 Mo SDRAM 133
RADEON 9200 SE 64 Mo
UBUNTU 5.04 with GNOME
Screen 0 - CRT - 1152x864 à 75 Hz
Screen 1 - TV – 800x600 à 60 Hz
--------------
fireglcontrol
--------------
Display Adaptater
    Card Name:    Radeon9200SE
    Bios Version:    8.15
    Chip Type:        ATI Radeon 9200SE (RV280 Yd)
    Chip Revision:    A12
    DAC Speed:    400 Mhz
    Memory Type:    DDR SDRAM
    Memory Size:    64 Mbyte
    Transfer Mode:    AGP 4x, SBA (AGP v2.0)
Display Driver
    Driver Version:    8.08.25
OpenGl
    OpenGL vendor string:     ATI Technologies Inc.
    OpenGL renderer string:     RADEON 9200SE DDR Generic
    OpenGL version string:     1.3.4769 (X4.3.0-8.8.25)   

--------------
Test fglrx
--------------
--------------
glxgears (in the background)
--------------
7640 frames in 5.0 seconds = 1528.000 FPS
7641 frames in 5.0 seconds = 1528.200 FPS
7642 frames in 5.0 seconds = 1528.400 FPS
7640 frames in 5.0 seconds = 1528.000 FPS
7640 frames in 5.0 seconds = 1528.000 FPS
7638 frames in 5.0 seconds = 1527.600 FPS
--------------
fgl_glxgears (in the background)
--------------
1169 frames in 5.0 seconds = 233.800 FPS
1168 frames in 5.0 seconds = 233.600 FPS
1173 frames in 5.0 seconds = 234.600 FPS
1170 frames in 5.0 seconds = 234.000 FPS
1170 frames in 5.0 seconds = 234.000 FPS
1170 frames in 5.0 seconds = 234.000 FPS
--------------
glxgears (in the foreground)
--------------
3762 frames in 5.0 seconds = 752.400 FPS
3761 frames in 5.0 seconds = 752.200 FPS
3761 frames in 5.0 seconds = 752.200 FPS
3761 frames in 5.0 seconds = 752.200 FPS
3761 frames in 5.0 seconds = 752.200 FPS
3761 frames in 5.0 seconds = 752.200 FPS
--------------
fgl_glxgears (in the foreground)
--------------
672 frames in 5.0 seconds = 134.400 FPS
686 frames in 5.0 seconds = 137.200 FPS
688 frames in 5.0 seconds = 137.600 FPS
674 frames in 5.0 seconds = 134.800 FPS
691 frames in 5.0 seconds = 138.200 FPS
687 frames in 5.0 seconds = 137.400 FPS

```
--------------
/etc/X11/xorg.conf
--------------
```

        Section "Files"
	FontPath	"unix/:7100"
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Module"	
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
		Option    "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection
# ===================== KEYBOARD
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"	
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr-latin9"
EndSection
# ===================== MOUSE
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"	
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
# ===================== MONITOR DISPLAY (screen0)
Section "Monitor"
	Identifier	"MicroScanE44"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen 0
	Option "DesktopSetup" "0x00000000"
	# === disable/enable XAA/DRI ===
        Option "no_accel"                   "no"
        Option "no_dri"                     "no"
	# === TV-out Management ===
        #Option "NoTV"                       "no"     
	#Option "CursorShadow" "1"
	#Option "TVStandard" "PAL-N"
	#Option "ConnectedMonitor" "TV"
	#Option "TVOutFormat" "Composite"
	#Option "TVHSizeAdj"                 "-10"     
    	#Option "TVVSizeAdj"                 "20"     
    	#Option "TVHPosAdj"                  "15"     
    	#Option "TVVPosAdj"                  "0"
	#Option "VideoOverlay" "on"     
    	#Option "TVHStartAdj"                "0"     
    	#Option "TVColorAdj"                 "0"     
    	#Option "GammaCorrectionI"           "0x06419064"
    	#Option "GammaCorrectionII"          "0x06419064"
	# === OpenGL specific profiles/settings ===
        Option "Capabilities"               "0x00000000"
	# === Video Overlay for the Xv extension ===
        Option "VideoOverlay"               "on"
	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#       will be disabled automatically
        Option "OpenGLOverlay"              "off"
	# === Center Mode (Laptops only) ===
        Option "CenterMode"                 "off"
	# === Pseudo Color Visuals (8-bit visuals) ===
        Option "PseudoColorVisuals"         "off"
	# === QBS Management ===
        Option "Stereo"                     "off"
        Option "StereoSyncEnable"           "1"
	# === FSAA Management ===
        Option "FSAAEnable"                 "no"
        Option "FSAAScale"                  "1"
        Option "FSAADisableGamma"           "no"
        Option "FSAACustomizeMSPos"         "no"
        Option "FSAAMSPosX0"                "0.000000"
        Option "FSAAMSPosY0"                "0.000000"
        Option "FSAAMSPosX1"                "0.000000"
        Option "FSAAMSPosY1"                "0.000000"
        Option "FSAAMSPosX2"                "0.000000"
        Option "FSAAMSPosY2"                "0.000000"
        Option "FSAAMSPosX3"                "0.000000"
        Option "FSAAMSPosY3"                "0.000000"
        Option "FSAAMSPosX4"                "0.000000"
        Option "FSAAMSPosY4"                "0.000000"
        Option "FSAAMSPosX5"                "0.000000"
        Option "FSAAMSPosY5"                "0.000000"
	# === Misc Options ===
        Option "UseFastTLS"                 "0"
        Option "BlockSignalsOnLock"         "on"
        Option "UseInternalAGPGART"         "no"
        Option "ForceGenericCPU"            "no"
    	Option "mtrr"                       "off"
EndSection

Section "Screen"
	Identifier	"DefaultScreen"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"MicroScanE44"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

# ===================== TV DISPLAY (screen1)
Section "Monitor"
	Identifier "tv"
	HorizSync 30.0-50.0
	VertRefresh 50.0-60.0
EndSection

Section "Device"
	Identifier	"ATI TV"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen 1
	Option "DesktopSetup" "0x00000000"
	# === disable/enable XAA/DRI ===
        Option "no_accel"                   "no"
        Option "no_dri"                     "no"
	# === TV-out Management ===
        Option "NoTV"                       "no"     
	#Option "CursorShadow" "1"
	Option "TVStandard" "PAL-N"
	Option "ConnectedMonitor" "TV"
	Option "TVOutFormat" "Composite"
	Option "TVHSizeAdj"                 "-10"     
    	Option "TVVSizeAdj"                 "20"     
    	Option "TVHPosAdj"                  "15"     
    	Option "TVVPosAdj"                  "0"
	#Option "VideoOverlay" "on"     
    	Option "TVHStartAdj"                "0"     
    	Option "TVColorAdj"                 "0"     
    	Option "GammaCorrectionI"           "0x06419064"
    	Option "GammaCorrectionII"          "0x06419064"
	# === OpenGL specific profiles/settings ===
        Option "Capabilities"               "0x00000000"
	# === Video Overlay for the Xv extension ===
        Option "VideoOverlay"               "on"
	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#       will be disabled automatically
        Option "OpenGLOverlay"              "off"
	# === Center Mode (Laptops only) ===
        Option "CenterMode"                 "off"
	# === Pseudo Color Visuals (8-bit visuals) ===
        Option "PseudoColorVisuals"         "off"
	# === QBS Management ===
        Option "Stereo"                     "off"
        Option "StereoSyncEnable"           "1"
	# === FSAA Management ===
        Option "FSAAEnable"                 "no"
        Option "FSAAScale"                  "1"
        Option "FSAADisableGamma"           "no"
        Option "FSAACustomizeMSPos"         "no"
        Option "FSAAMSPosX0"                "0.000000"
        Option "FSAAMSPosY0"                "0.000000"
        Option "FSAAMSPosX1"                "0.000000"
        Option "FSAAMSPosY1"                "0.000000"
        Option "FSAAMSPosX2"                "0.000000"
        Option "FSAAMSPosY2"                "0.000000"
        Option "FSAAMSPosX3"                "0.000000"
        Option "FSAAMSPosY3"                "0.000000"
        Option "FSAAMSPosX4"                "0.000000"
        Option "FSAAMSPosY4"                "0.000000"
        Option "FSAAMSPosX5"                "0.000000"
        Option "FSAAMSPosY5"                "0.000000"
	# === Misc Options ===
        Option "UseFastTLS"                 "0"
        Option "BlockSignalsOnLock"         "on"
        Option "UseInternalAGPGART"         "no"
        Option "ForceGenericCPU"            "no"
    	Option "mtrr"                       "off"
EndSection

Section "Screen"
	Identifier "tvscreen"
	Device "ATI TV"
	Monitor "tv"
	DefaultColorDepth 24
	Subsection "Display"
		Modes "800x600" "Interlace"
		Depth 24
	EndSubsection
EndSection
# ===================== SERVERLAYOUT
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"DefaultScreen"
	Screen 		"tvscreen" RightOf "DefaultScreen"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
EndSection

```

---

### Post by cyberlab on 2005-05-07
Does this option in xorg.conf section device can solve my problem

Option "CursorShadow" "1"

I try to comment this line but nothing. What is the syntax for this option, is there "0", "off" or "false" for disable

---

