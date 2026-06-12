---
title: "x.org problem with screen size"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by mohrt on 2005-04-14
Hi,

I have a multihead setup that has been running fine on Warty. As soon as I upgraded to Hoary, the screen size on my second monitor isn't quite right.

I have two Samsung SyncMaster 955DF monitors, the first with a Nvidia card and the second with a voodoo3 card. Both monitors are running at 1600x1200 resolution. After I upgraded to Hoary, the screen width on my second monitor is wider than the actual resolution by about an inch. When I move my mouse to the left or right side of the screen, the entire window will slide around to see the rest of the screen. What would cause this extra size?

Here is my xorg.conf:

```

Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option		"StandbyTime" "10"
	Option		"SuspendTime" "20"
	Option		"OffTime" "30"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/CID"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "xtrap"
	Load  "type1"
	Load  "speedo"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	#DisplaySize	  360   270	# mm
	Identifier   "Monitor1"
	VendorName   "SAM"
	ModelName    "SyncMaster"
	HorizSync   30.0 - 85.0
	VertRefresh 50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "DigitalVibrance"    	# <i>
        #Option     "NoFlip"             	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        Option     "NoLogo"             	# [<bool>]
        #Option     "UBB"                	# [<bool>]
        #Option     "Stereo"             	# <i>
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        Option     "NvAGP"              	"1" # <i>
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ConnectedMonitor"   	# <str>
        #Option     "ConnectedMonitors"  	# <str>
        #Option     "TVStandard"         	# <str>
        #Option     "TVOutFormat"        	# <str>
        Option     "RenderAccel"        	"true" # [<bool>]
        #Option     "CursorShadow"       	# [<bool>]
        #Option     "CursorShadowAlpha"  	# <i>
        #Option     "CursorShadowXOffset" 	# <i>
        #Option     "CursorShadowYOffset" 	# <i>
        #Option     "UseEdidFreqs"       	# [<bool>]
        #Option     "FlatPanelProperties" 	# <str>
        #Option     "TwinView"           	# [<bool>]
        #Option     "TwinViewOrientation" 	# <str>
        #Option     "SecondMonitorHorizSync" 	# <str>
        #Option     "SecondMonitorVertRefresh" 	# <str>
        #Option     "MetaModes"          	# <str>
        #Option     "UseInt10Module"     	# [<bool>]
        #Option     "NoTwinViewXineramaInfo" 	# [<bool>]
        #Option     "NoRenderExtension"  	# [<bool>]
        #Option     "Overlay"            	# [<bool>]
        #Option     "CIOverlay"          	# [<bool>]
        #Option     "ForceEmulatedOverlay" 	# [<bool>]
        #Option     "TransparentIndex"   	# <i>
        #Option     "OverlayDefaultVisual" 	# [<bool>]
        #Option     "NvEmulate"          	# <i>
        #Option     "NoBandWidthTest"    	# [<bool>]
        #Option     "CustomEDID-CRT-0"   	# <str>
        #Option     "CustomEDID-CRT-1"   	# <str>
        #Option     "CustomEDID-DFP-0"   	# <str>
        #Option     "CustomEDID-DFP-1"   	# <str>
        #Option     "CustomEDID-TV-0"    	# <str>
        #Option     "CustomEDID-TV-1"    	# <str>
        #Option     "TVOverScan"         	# <f>
        #Option     "IgnoreDisplayDevices" 	# <str>
        #Option     "MultisampleCompatibility" 	# [<bool>]
        #Option     "RegistryDwords"     	# <str>
        #Option     "NoPowerConnectorCheck" 	# [<bool>]
        #Option     "AllowDFPStereo"     	# [<bool>]
        #Option     "XvMCUsesTextures"   	# [<bool>]
        #Option     "HorizSync"          	# <str>
        #Option     "VertRefresh"        	# <str>
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "Unknown Board"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "UsePIO"             	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "NoSLI"              	# [<bool>]
        #Option     "TexturedVideo"      	# [<bool>]
        #Option     "DRI"                	# [<bool>]
	Identifier  "Card1"
	Driver      "tdfx"
	VendorName  "3Dfx Interactive, Inc."
	BoardName   "Voodoo 3"
	BusID       "PCI:0:9:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor1"
	DefaultColorDepth 24
	SubSection "Display"
		Depth     1
	EndSubSection
	SubSection "Display"
		Depth     4
	EndSubSection
	SubSection "Display"
		Depth     8
	EndSubSection
	SubSection "Display"
		Depth     15
	EndSubSection
	SubSection "Display"
		Depth     16
	EndSubSection
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultColorDepth 24
	SubSection "Display"
		Depth     1
	EndSubSection
	SubSection "Display"
		Depth     4
	EndSubSection
	SubSection "Display"
		Depth     8
	EndSubSection
	SubSection "Display"
		Depth     15
	EndSubSection
	SubSection "Display"
		Depth     16
	EndSubSection
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

```

Thanks for any help!

---

### Post by mohrt on 2005-04-14
I'll reiterate the problem a bit, the virtual screen size is slightly larger than the actual screen size, which requires me to slide my mouse off the edge of the screen to see the left or right side. How do I make the virtual screen the same size as the actual screen, as it was before upgrading to Hoary? I tried the following but didn't seem to help anything:

```
Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultColorDepth 24
        SubSection "Display"
                Depth     24
                Modes "1600x1200"
                ViewPort 0 0
                Virtual 1600 1200
        EndSubSection
EndSection
```

Thanks

---

