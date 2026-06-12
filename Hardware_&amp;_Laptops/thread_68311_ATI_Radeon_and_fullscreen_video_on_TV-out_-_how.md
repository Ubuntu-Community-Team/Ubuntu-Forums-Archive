---
title: "ATI Radeon and fullscreen video on TV-out - how?"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by Ensnared on 2005-09-22
Hi,
 
 I'm trying to find out how to set up fullscreen video on TV-out on my Radeon 9800 card. I got 3D working nicely without too much hassle, and TV out is working since I have my desktop image on the TV. Apparently though, getting video output to the TV isn't quite as easy, and what I want is to have any video-file played display in fullscreen on my TV (just like the Theater-mode in the Windows driver-settings).
 
I've tried searching this forum as well as google, and also tried posting on the Rage3d forums to no avail - I can't find any guide to setting this up, or even information about wether it's possible or not.
 
What I've found out is that I may need to run 2 X-servers (one for the monitor and one for the TV), and if that's the case then what I need help with is finding out how my xorg.conf-file should look. I may not need to do it this way though, I have no idea, which is why I'm asking here [img]http://www.rage3d.com/board/images/smilies/smile.gif[/img]
 
 I've been using Linux for a long time, but this is a completely unfamiliar territory for me, so any help would be appreciated.
 
 Some relevant info:
 Card: Radeon 9800 (128MB)
 Monitor: 19" Iiyama Vision Master Pro 454 (HM903DT A)
 TV: 32" Panasonic Widescreen
 Distro: Ubuntu 5.04 "Hoary"
 Kernel: 2.6.10 (custom)
 X-Window System: x.org 6.8.2
 
My current xorg.conf:
```
Section "dri"
	Mode 0666
EndSection

Section "Module"
	Load		"dbe" # Double buffer extension
	SubSection "extmod"
		Option	"omit xfree86-dga" # don't initialise the DGA extension
	EndSubSection
	Load		"type1"
	Load		"freetype"
	Load		"glx" # libglx.a
	Load		"dri" # libdri.a
EndSection

Section "Files"
	RgbPath		"/usr/X11R6/lib/X11/rgb"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc/"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "ServerFlags"
EndSection

Section "InputDevice"
	Identifier "Keyboard1"
	Driver	 "kbd"
	Option "AutoRepeat" "500 30"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "no"
#	Option "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier "Mouse1"
	Driver	 "mouse"
	Option "Protocol"	"ImPS/2"
	Option "Device"	 "/dev/input/mice"
	Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier "Iiyama HM903DTA"
	HorizSync   30-130
	VertRefresh 50-200
	Option "DPMS"
EndSection

Section "Device"
	Identifier "Standard VGA"
	VendorName "Unknown"
	BoardName "Unknown"
	Driver	 "vga"
EndSection

# === ATI device section ===

Section "Device"
	Identifier	"ATI Graphics Adapter"
	Driver		"fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor ===
#	Option				"NoDDC"
# === disable/enable XAA/DRI ===
	Option "no_accel"		"no"
	Option "no_dri"			"no"
# === misc DRI settings ===
	Option "mtrr"	 	"off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
	Option "DesktopSetup"		"(null)"
	Option "ScreenOverlap"		"0"
# === TV-out Management ===
	Option "TVFormat"		"PAL-B"
	Option "TVStandard"		"PAL-SCART"
	Option "TVHSizeAdj"		"0"
	Option "TVVSizeAdj"		"0"
	Option "TVHPosAdj"		"0"
	Option "TVVPosAdj"		"0"
	Option "TVHStartAdj"		"0"
	Option "TVColorAdj"		"0"
	Option "GammaCorrectionI"	"0x06419064"
	Option "GammaCorrectionII"	"0x06419064"
# === OpenGL specific profiles/settings ===
	Option "Capabilities"		"0x00000000"
# === Video Overlay for the Xv extension ===
	Option "VideoOverlay"		"on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#	 will be disabled automatically
	Option "OpenGLOverlay"		"off"
# === Center Mode (Laptops only) ===
	Option "CenterMode"		"off"
# === Pseudo Color Visuals (8-bit visuals) ===
	Option "PseudoColorVisuals"	"off"
# === QBS Management ===
	Option "Stereo"			"off"
	Option "StereoSyncEnable"	"1"
# === FSAA Management ===
	Option "FSAAEnable"		"no"
	Option "FSAAScale"		"1"
	Option "FSAADisableGamma"	"no"
	Option "FSAACustomizeMSPos"	"no"
	Option "FSAAMSPosX0"		"0.000000"
	Option "FSAAMSPosY0"		"0.000000"
	Option "FSAAMSPosX1"		"0.000000"
	Option "FSAAMSPosY1"		"0.000000"
	Option "FSAAMSPosX2"		"0.000000"
	Option "FSAAMSPosY2"		"0.000000"
	Option "FSAAMSPosX3"		"0.000000"
	Option "FSAAMSPosY3"		"0.000000"
	Option "FSAAMSPosX4"		"0.000000"
	Option "FSAAMSPosY4"		"0.000000"
	Option "FSAAMSPosX5"		"0.000000"
	Option "FSAAMSPosY5"		"0.000000"
# === Misc Options ===
	Option "UseFastTLS"		"0"
	Option "BlockSignalsOnLock"	"on"
	Option "UseInternalAGPGART"	"no"
	Option "ForceGenericCPU"	"no"
	Option "KernelModuleParm"	"agplock=0"
# === Disable fastwrite ===
	Option  "AGPMask"	"0x00000010"	# For AGP v1-v2
	Option  "AGPv3Mask"  "0x00000002"	# For AGP v3 (settings both is fine)

	BusID "PCI:3:0:0"	# vendor=1002, device=4e48
	Screen 0
EndSection

Section "Screen"
	Identifier "Screen0"
	Device	 "ATI Graphics Adapter"
	Monitor	 "Iiyama HM903DTA"
	DefaultDepth 24
	Subsection "Display"
		Depth	 24
		Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
		ViewPort	0 0 # initial origin if mode is smaller than desktop
	EndSubsection
EndSection


Section "ServerLayout"
	Identifier "Server Layout"
	Screen "Screen0"
	InputDevice "Mouse1" "CorePointer"
	InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###
```

 Thanks in advance [img]http://www.rage3d.com/board/images/smilies/smile.gif[/img]

---

