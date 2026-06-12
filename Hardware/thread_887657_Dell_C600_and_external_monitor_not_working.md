---
title: "Dell C600 and external monitor not working"
date: 2008-08-12
forum: Hardware
---

### Post by KoolPenguin on 2008-08-12
This seems to have been asked dozens of times, but hey might as well as for my specs, ya never know.

Using a Dell Latitude C600 w/ATI Rage Mobility and a Dell 2007WFP monitor. I cannot seem to get it to display to the external monitor once X11 session starts. I'm trying to get this to work with Zenwalk as it runs faster on this laptop than ubuntu. I also posted this on the Zenwalk forums...

Here is my xorg.conf:

> # **********************************************************************
# Files section -- This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/OTF"
	FontPath     "/usr/share/fonts/Type1"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/75dpi/:unscaled"
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************

Section "Module"
	Load  "synaptics"
	Load  "dri"
	Load  "dbe"
	Load  "xtrap"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "GLcore"
	Load  "type1"
	Load  "freetype"
EndSection

# **********************************************************************
# Server flags section
# **********************************************************************

Section "ServerFlags"
#    Option     "NoTrapSignals"
#    Option     "DontVTSwitch"
#    Option     "DontZap"
#    Option     "DontZoom"
#    Option     "DisableVidModeExtension"
#    Option     "AllowNonLocalXvidtune"
#    Option     "DisableModInDev"
#    Option     "AllowNonLocalModInDev"
#    Option      "blank time"    "10"    # 10 minutes
#    Option      "standby time"  "20"
#    Option      "suspend time"  "30"
#    Option      "off time"      "60"

# Option   "EstimateSizesAggresively" "0"

EndSection


# **********************************************************************
# DRI section
# **********************************************************************

Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
EndSection


# **********************************************************************
# Extensions section
# **********************************************************************

Section "Extensions"
        Option "Composite" "Enable"
EndSection


# **********************************************************************
# Keyboard section
# **********************************************************************

Section "InputDevice"
	Identifier	"Keyboard1"
	Driver	"kbd"
#	Option     "Protocol"      "Xqueue"
#	Option     "AutoRepeat"    "500 5"
#	Option     "Xleds" "1 2 3"
#	Option     "XkbDisable"

	Option     "XkbRules"      "xorg"
	Option     "XkbModel"      "pc105"
	Option     "XkbLayout"     ""
#	Option     "XkbVariant"    "us"
	Option     "XkbOptions"    ""
EndSection


# **********************************************************************
# Pointers section
# **********************************************************************

Section "InputDevice"

# Identifier and driver
	Identifier "Mouse1"
	Driver	     "mouse"
	Option	     "Protocol" "Auto"
	Option	     "Device" "/dev/mouse"
#	Option     "Protocol" "Xqueue"
#	Option     "BaudRate" "9600"
#	Option     "SampleRate"	"150"
#	Option     "Emulate3Buttons"
#	Option     "Emulate3Timeout" "50"
#	Option     "ChordMiddle"
	Option     "ZAxisMapping" "4 5"
EndSection

Section "InputDevice" 
	Identifier    "Pad1" 
	Driver        "synaptics" 
	Option           "Protocol" "auto-dev" 
	Option           "Device" "/dev/tp1" 
	Option        "LeftEdge"      "1700" 
	Option        "RightEdge"     "5300" 
	Option        "TopEdge"       "1700" 
	Option        "BottomEdge"    "4200" 
	Option        "FingerLow"     "25" 
	Option        "FingerHigh"    "30" 
	Option        "MaxTapTime"    "180" 
	Option        "MaxTapMove"    "220" 
	Option        "VertScrollDelta" "100" 
	Option        "MinSpeed"      "0.09" 
	Option        "MaxSpeed"      "0.18" 
	Option        "AccelFactor"   "0.0015" 
	Option        "SHMConfig"     "on" 
EndSection 

# **********************************************************************
# Monitor section
# **********************************************************************
Section "Monitor"
	Identifier "LCD Panel"
	VendorName "DXS"
	ModelName  "DXS:1313"
	HorizSync 31.5 - 50.0
	VertRefresh 40-90
	Option	"UseEdidFreqs" "1"
	Option	"ReducedBlanking"
	Option	"DPMS"
EndSection

Section "Monitor"
	Identifier "DELL 2007WFP"
	VendorName "DEL"
	ModelName  "DELL 2007WFP"
	Modeline   "1680x1050_59.954" 146.250000 1680 1784 1960 2240 1050 1053 1059 1089 +HSync -VSync	
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
	Option      "ReducedBlanking"
EndSection

# **********************************************************************
# Graphic devices section
# **********************************************************************

# Any number of graphic devices sections may be present

Section "Device"
	Identifier "ATI|Rage Mobility M3"
	Driver "r128"
	VideoRam 8192
	BusID  "PCI:1:0:0"
	Option "EnablePageFlip" "true"
	Option "AGPFastWrite" "true"
	Option "RenderAccel" "true"
	Option "AGPMode" "2" 
EndSection

# **********************************************************************
# Screen section
# **********************************************************************

Section "Screen"
	Identifier "Screen0"
	Device "ATI|Rage Mobility M3"
	Monitor "LCD Panel"
	DefaultDepth 24
	Subsection "Display"
	 Depth       16
	 Modes  "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
	Subsection "Display"
	 Depth       24
	 Modes  "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
EndSection
Section "Screen"
	Identifier "Screen1"
	Device "ATI|Rage Mobility M3"
	Monitor "DELL 2007WFP"
	DefaultDepth 24
	Subsection "Display"
         Depth       16
         Modes "1680x1050_59.954" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
	Subsection "Display"
         Depth       24
         Modes "1680x1050_59.954" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
EndSection

# **********************************************************************
# ServerLayout section
# **********************************************************************
Section "ServerLayout"
	Identifier		"Panel"
	Screen			"Screen0"
	InputDevice		"Mouse1" "CorePointer"
	InputDevice		"Pad1" "SendCoreEvents"
	InputDevice		"Keyboard1" "CoreKeyboard"
EndSection
Section "ServerLayout"
	Identifier		"External"
	Screen			"Screen1"
	InputDevice		"Mouse1" "CorePointer"
	InputDevice		"Pad1" "SendCoreEvents"
	InputDevice		"Keyboard1" "CoreKeyboard"
EndSection
- Laptop set to the lcd panel only, I get a display and the Fn keys work (except the CRT/LCD).
- Laptop set to external monitor only, works until X session starts. Then defaults back to the panel and no Fn keys.
- Laptop set to display to both, works until X session starts and then I get no display on either.

I don't know what else I could try, maybe someone going over my xorg.conf could suggest something else.

Thanks.

---

### Post by KoolPenguin on 2008-08-14
Bumping for help...

I did find this link with info on getting the external monitor to work, but it does not seem to work with Zenwalk 5.2 or ubuntu Hardy.  Does anyone know if it will work with ubuntu 7.10 or what changes may need to be made?

[http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html]("http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html")

Thanks

---

