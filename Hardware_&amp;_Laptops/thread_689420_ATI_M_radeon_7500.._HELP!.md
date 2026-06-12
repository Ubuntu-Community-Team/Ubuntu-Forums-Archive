---
title: "ATI M radeon 7500.. HELP!"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by adde on 2008-02-06
I am struggling with my ATI graphics card, and have read thread after thread without success.
I have a Acer travelmate with a Mobility Radeon 7500, and recently upgraded to Gutsy from Feisty. When running feisty I was using Beryl, and it worked even if it wasn't perfect.
Now in gutsy I can't enable any cool stuff in advanced desktop effect settings. All the 
boxes are grey (disabled).

Is there any good graphic drivers I can use? Fglrx maybe?
I have read that there should be a driver available in "Manage 3rd party software", but not for me.

My xorg.conf looks like this:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "AGPMode" "4"
        Option          "AGPSize" "64" # default: 8
        Option          "RingSize" "8"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "True"
        Option          "EnableDepthMoves" "True"
        Option          "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
SubSection "Display"
		Depth		1
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes 		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

glxgears show the gears spinning with the following info:

```

adde@adde-laptop:~$ glxgears -info
GL_RENDERER   = Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
GL_VERSION    = 1.3 Mesa 7.0.1
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
7751 frames in 5.0 seconds = 1543.004 FPS
7734 frames in 5.0 seconds = 1541.715 FPS
7726 frames in 5.0 seconds = 1544.202 FPS
7700 frames in 5.0 seconds = 1525.229 FPS
4294 frames in 5.1 seconds = 842.703 FPS
2517 frames in 5.3 seconds = 477.122 FPS
5380 frames in 5.3 seconds = 1008.104 FPS
1080 frames in 5.4 seconds = 200.869 FPS
1320 frames in 5.5 seconds = 240.644 FPS
7028 frames in 5.0 seconds = 1401.579 FPS
7980 frames in 5.0 seconds = 1587.449 FPS
13807 frames in 5.0 seconds = 2753.917 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


```

And..

```

adde@adde-laptop:~$ glxgears
6025 frames in 5.0 seconds = 1194.334 FPS
6046 frames in 5.1 seconds = 1189.223 FPS
5980 frames in 5.0 seconds = 1187.723 FPS
6000 frames in 5.1 seconds = 1186.843 FPS
5118 frames in 5.1 seconds = 1004.124 FPS
1920 frames in 5.3 seconds = 364.434 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 64574 requests (64230 known processed) with 2 events remaining.

```


~1500 FPS was the original window size, ~200 I got when making the window bigger and ~2700 FPS when I made the window really small.

fglrxinfo shows:

```

adde@adde-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```


Tried to add as much as I could think of to this post.. :)
Anyone have any suggestions to all the cool 3D effects working on my pc?
Oh.. I have CCSM 0.5.2 installed.
Open for ideas! :)

---

### Post by adde on 2008-02-07
Now I have got compiz working with the cube and wobbly windows. The strange thing is that the only thing I did was installing Envy ( read in a thread that Envy will automaticly detect graphic card and install appropriate driver) , but Envy didn't succed in detecting my card, so I uninstalled envy again. Then compiz started to work... Strange..
Can someone explain that? :)

The only problem I have now is that when I open advanced desktop effects settings I cannot change anything. Everything is grey.. Disabled. 
Does anyone know how to make all the effects (and things in ccsm) available again?

---

### Post by ardnetih on 2008-04-07
Hi all,

Let me start with information about my setup:

Model: Compaq Presario 2800 laptop
Processor: Pentium 4-M 1.4 GHz
Memory: 1.5GB
Video card: ATI Radeon Mobility 7500

I have been running Fiesty perfectly for quite some time now with a resolution of 1024x768@60 with a color depth of 24. All desktop effects and 3D stuff was working fine and I had a good frame rate too. Then I upgraded to Gusty and since then I have been forced to run on a resolution of 800x600 and color depth 16. Here are the steps I took to try to resolve the issue (no luck so far):

1. Ran through reconfiguring xserver via: ```
sudo dpkg-reconfigure xserver-xorg
```I set all the variables correctly, chose the "radeon" driver to use, chose the correct resolution "1024x768", chose the correct monitor type, refresh rate and saved. Once I restarted gdm (using ctrl-alt-backspace) my screen was all shaky and shifted to the left. I changed the resolution back to 800x600 and all looked fine. This is how the xorg.conf looked like after I ran through the re-config:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"LVDSBiosNativeMode" "FALSE"
	Option		"GARTSize" "64"
	Option		"AGPSize" "64"
	Option		"AGPMode" "4"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode" "8"
	Option		"AGPFastWrite" "True"
	Option		"EnablePageFlip" "true"
	Option		"EnableDepthMoves" "true"
	Option		"UseInternalAGPGART" "no"
	Option		"BackingStore" "on"
	Option		"UseInternalAGPGART" "no"
	Option		"DMAForXv" "true"
	Option		"AccelMethod" "XAA"
	Option		"ColorTiling" "on"
	Option		"AccelDFS" "true"
	Option		"TripleBuffer" "true"
	Option		"DynamicClocks" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option		"AIGLX" "true"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```


2. I had a saved copy of xorg.conf from Fiesty, so I backed up the existing one, replaced it with copy from Fiesty and restarted gdm. This also did not make any difference. I am still stuck with the 800x600 mode. Here is the xorg.conf from Fiesty, which I am now running in my Gutsy install:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	32768
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Any suggestions will be welcomed and tested. Thanks for helping.

---

### Post by averageidiot on 2008-04-07
try this, post # 14

worked for me


[http://ubuntuforums.org/showthread.php?t=717103&page=2](http://ubuntuforums.org/showthread.php?t=717103&page=2)

---

