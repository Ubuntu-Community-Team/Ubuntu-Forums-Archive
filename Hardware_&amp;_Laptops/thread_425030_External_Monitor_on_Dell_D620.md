---
title: "External Monitor on Dell D620"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by wiggumon on 2007-04-27
Hello all,

First, I would like to say thanks to all the posters that have placed "how-to's", tutorials, and links on this site. Just by doing some searching I have been able to really get Ubuntu the way I want it...almost. 

I am having some trouble with my external monitor on my laptop. I have edited my xorg.conf file and the external monitor seems to work fine on boot-up. I have my email open on my "main" screen (the dell laptop screen) and FireFox open on my external LCD. I have two problems though. 

One is that when I try to use a desktop background it doesn't appear correctly on either screen. It gets centered between both screens. I have tried "zoom", "scaled", and the rest and none of them appear correctly. The background is always off in some way. On a side note. The screen saver only appears on the laptop screen.

The second problem is on shutdown. The "primary" screen is the dell laptop screen (I think) and when I shutdown the external LCD becomes the primary. In other words my laptop screen flickers and goes blank while the LCD has the Ubuntu shutdown message. When I am not using an external LCD and shutdown my laptop just goes blank. No visuals at all.

I am sure that I am missing something in my xorg.conf but I just can't seem to find it. I have posted my xorg.conf below. Any help would be great.

~wiggumon

```

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "xtrap"
	Load  "glx"
	Load  "GLcore"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "InternalMonitor"
	VendorName   "DEL"
	ModelName    "DELL 1907FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "ExternalMonitor"
	VendorName   "DEL"
	ModelName    "DELL 1907FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "InternalCard"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option	"MonitorLayout" "CRT,LFP"
	Screen 0
EndSection

Section "Device"
	Identifier  "ExternalCard"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option	"MonitorLayout" "CRT,LFP"
	Screen 1
EndSection

Section "Screen"
	Identifier "InternalScreen"
	Device     "InternalCard"
	Monitor    "InternalMonitor"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "ExternalScreen"
	Device     "ExternalCard"
	Monitor    "ExternalMonitor"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "DualHead"
	Screen      0  "InternalScreen" 0 0
	Screen      1  "ExternalScreen" RightOf "InternalScreen"
	Option "Xinerama" "true"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

```

---

### Post by wiggumon on 2007-04-27
Oops, I forgot to add this. I am using:

Dell Latitude D620 with the Intel Chipset
1 Gig of Ram

~wiggumon

---

### Post by gario on 2007-04-27
Hmm, I have almost the exact same setup with a D600 and external CRT.

I use the "tiled" setting for my background, which isn't ideal, but at least the background makes it all the way across.

My laptop display does work correctly as primary when shutting down.  Not sure what's missing from your xorg.conf.  The only real difference I see with mine is I also have a "ServerLayout" option:

```

	Option	       "Clone" "on"

```

so that I can start without an external monitor, then plug in the external display after logging in if I want to do clone mode.

The other difference I see is the "MonitorLayout" setting under the "Device" section.  I have:

```

	Option "MonitorLayout" "LVDS, Auto"

```

I think this allows me to run a single monitor when I login without the external monitor attached.  You might try tweaking that setting and checking the man pages for it.

Here is my full xorg.conf if it helps:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen	    0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option	       "Xinerama" "on"
	Option	       "Clone" "on"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	Option	     "DPMS"
	HorizSync    30 - 85
	VertRefresh  50 - 160
EndSection

Section "Device"
	Identifier  "Radeon0"
	Driver      "radeon"
	Option	    "DesktopSetup" "horizontal"
	Option "MonitorLayout" "LVDS, Auto"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "DisableGLXRootClipping" "true"
	Option "AddARGBGLXVisuals" "true"
	Option "AllowGLXWithComposite" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "EnablePageFlip" "true"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "Radeon1"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
	Screen	    1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Radeon0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Radeon1"
	Monitor    "Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1400x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Group	     0
	Mode         0666
EndSection



```

---

### Post by wiggumon on 2007-04-27
Thanks gario, I am going to try this out ASAP.

~wiggumon

---

### Post by wiggumon on 2007-04-28
Well, at least it's getting closer. I have some more tweaking to do though. I added the "clone" "on" option and "LVDS" "auto" for the external monitor. It's kind of 50/50 whether Ubuntu acts up. I'll keep trying over the weekend and post my results. At least I haven't broken anything yet. :)

~wiggumon

---

