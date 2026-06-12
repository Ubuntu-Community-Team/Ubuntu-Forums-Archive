---
title: "Inspiron 700m - Intel i810 graphics card - dual monitor problem"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by alperyilmaz on 2007-05-19
Hi,
I have Dell Inspiron 700m laptop with Intel Graphics driver. The device identifier is Intel82852/855GM Integrated Graphics Device and Driver is "i810". I was trying to set-up dual monitor system  so that I can use an external monitor as an extended desktop. I surfed though the Ubuntuforums and there were several suggestions to add some lines into Xorg.conf and tried most of them and it didn't work. In each case, after updating Xorg.conf file, I re-started the X server and it crashed with blue screen which writes X server was shutdown due to error. 

I am using Ubuntu 7.04

I need advice from experienced users. Should I give-up?  Is there no way to make i810 run dual-monitor under Ubuntu? OR is there a "working" work-around for my case?

I'm posting contents of different Xorg.conf files that I tried.  

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
#	Load	"glx"
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
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller 0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller 0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	ModelName "Dell P991"
	Option "DPMS"
	HorizSync 31.5 - 90.0
	VertRefresh 59.9 - 60.1
	ModeLine "1920x1200" 154.0 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller 0"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller 0"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1280x1024" "1024x768"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Dual-Monitor Layout"
	Screen 0	"Laptop Screen" 0 0
	Screen 1	"External Screen" RightOf "Laptop Screen"
	Option		"Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection 
```

Here's another configuration I tried:
```
Section "ServerLayout"
        Identifier     "MultiheadLayout"
        Screen      0  "Screend0" 
        Screen      1  "Screend1" RightOf "Screend0"
        InputDevice     "Generic Keyboard" "CoreKeyboard"
        InputDevice     "Configured Mouse" "CorePointer"
        InputDevice     "Synaptics Touchpad" "AlwaysCore"
        Option      "Xinerama" "on"
EndSection


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
	Identifier	"videocardd0"
	Driver		"i810"
        VendorName      "Intel"
        BoardName       "855 GM"
	BusID		"PCI:0:2:0"
	Option "UseBIOS" "false"
	Option "VBERestore" "true" 
	Option "MonitorLayout" "CRT,LFP"
	Option "Display" "LFP"
        option "DisplayInfo" "FALSE"
	Option "DevicePresence" "TRUE"
	Screen 0
EndSection

Section "Device"
	Identifier	"videocardd1"
	Driver		"i810"
        VendorName      "Intel"
        BoardName       "855 GM"
	BusID		"PCI:0:2:0"
	Option "UseBIOS" "false"
	Option "VBERestore" "true"
	Option "MonitorLayout" "CRT,LFP"
	Option "Display" "CRT" 
	option "DisplayInfo" "FALSE"
	Option "DevicePresence" "TRUE"
	Screen 1
EndSection

#Section "Device"
#	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device 1"
#	Driver		"i810"
#	BusID		"PCI:0:2:0"
#	Screen 1
#	Option "DDCMode" "True"
#	Option "MonitorLayout" "LFP, CRT"
#EndSection

Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    30-82
        ModelName    "Local LCD Panel 1280X800@60HZ"
        Option       "DPMS"
        VendorName   "--> LCD"
        VertRefresh  57-60
        Modeline      "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "--> CRT"
        ModelName    "CRT 1280x1024"
        HorizSync    31.5 - 67.0
        VertRefresh  70.0 - 75.0
        Option      "dpms"
EndSection
 

Section "Screen"
        Identifier "Screend0"
        Device     "Videocardd0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screend1"
        Device     "Videocardd1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
		Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI" 
	Mode	0666
EndSection
```

And the final configuration I tried:
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
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
#       Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Identifier      "Intel-LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "MonitorLayout" "CRT, CRT+LFP"
EndSection
 
Section "Device"
        Identifier      "Intel-VGA"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
        Option "MonitorLayout" "CRT, CRT+LFP"
EndSection
 
Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection
 
Section "Monitor"
        Identifier      "CRT"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection
 
Section "Screen"
        Identifier      "LCD-Screen"
        Device          "Intel-LCD"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
 
Section "Screen"
        Identifier      "CRT-Screen"
        Device          "Intel-VGA"
        Monitor         "CRT"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200"
        EndSubSection
EndSection
 
 
Section "ServerLayout"
        Identifier      "Multihead"
        Screen          0 "LCD-Screen"
        Screen          1 "CRT-Screen" RightOf "LCD-Screen"
        Option "Xinerama" "on"
        Option "Clone" "off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection 
```

---

### Post by veloce on 2007-05-24
Try your first one again but change DFP to CRT in your monitor layout line.  I think DFP has to be connected digitally - using DVI connector.

Make sure there is no space after the comma in that line - it's interpreted as a null monitor.

---

### Post by Seeker84 on 2007-05-25
Hey, I'm using edgy eft but you can try what I did.  I would suggest taking the DFP ,LFP and make it CRT,LFP.  Check out in my post

[http://ubuntuforums.org/showthread.php?p=2712667#post2712667](http://ubuntuforums.org/showthread.php?p=2712667#post2712667)

and I don't know if order is an issue but I made sure the BusID and screen were towards the bottom the the device sections

I'm also using a dell inspiron 700m

---

### Post by veloce on 2007-05-26
> **Seeker84 said:**
> 
and I don't know if order is an issue but I made sure the BusID and screen were towards the bottom the the device sections


Yes, order is important.  With Dell laptops, at least, LFP has to be pipe B (i.e. second).

---

### Post by alperyilmaz on 2007-05-27
Unfortunately, it didn't work. X crashed as usual with same error message. I think I'll give up, maybe 3-4 kernel versions later setting up dual monitor will be easy.

I pasted Warning and Error messages from Xorg.0.log file:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): Bad V_BIOS checksum
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) intel(0): Failed to allocate texture space.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

---

### Post by veloce on 2007-05-27
> **alperyilmaz said:**
> Unfortunately, it didn't work. X crashed as usual with same error message. I think I'll give up, maybe 3-4 kernel versions later setting up dual monitor will be easy.

I pasted Warning and Error messages from Xorg.0.log file:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): Bad V_BIOS checksum
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) intel(0): Failed to allocate texture space.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

You are using the "intel" driver aren't you?  I can't get that driver to work with dual monitors.  Switch back to the "i810" driver (and install 915resolution if necessary).

---

