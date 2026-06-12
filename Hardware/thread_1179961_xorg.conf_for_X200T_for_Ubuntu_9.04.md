---
title: "xorg.conf for X200T for Ubuntu 9.04"
date: 2009-06-06
forum: Hardware
---

### Post by nimonika on 2009-06-06
Please could someone pass me the xorg.conf for X2OOT. My earlier one does not seem to work with the upgraded install, even after installing wacom and the linux wacom drivers.

Earlier xorg.conf:

 # Uncomment the following section if you you have a TabletPC that upports touch

Section "Monitor"
	Identifier    "Configured Monitor"
EndSection

Section "Monitor"
	Identifier    "HDMI-1"
	Option        "Ignore" "True"
EndSection

Section "Monitor"
	Identifier    "HDMI-2"
	Option        "Ignore" "True"
EndSection

Section "Screen"
	Identifier    "Default Screen"
	Monitor        "Configured Monitor"
	Device        "Configured Video Device"
	DefaultDepth     24
	SubSection "Display"
		Modes "1280x800" "1024x768"
		Virtual	2704 1050
	EndSubSection
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "stylus"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "eraser"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "cursor"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "pad"
	Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
	Option        "Type"          "pad"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "touch"
	Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
	Option        "Type"          "touch"
	Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
	Option "BottomX" "915"
	Option "BottomY" "940"
	Option "TopX" "48"
	Option "TopY" "90"
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice   "stylus"  "SendCoreEvents"
	InputDevice   "eraser"  "SendCoreEvents"
	InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
	InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
	InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this typeEndSection
EndSection

Section "Device"
	Identifier    "Configured Video Device"
	Driver        "intel"
	Option        "monitor-HDMI-1" "HDMI-1"
	Option        "monitor-HDMI-2" "HDMI-2"
EndSection

---

