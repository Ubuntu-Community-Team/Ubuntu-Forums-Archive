---
title: "915resolution Problems"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by DiamondX on 2007-02-24
Hi, I have a Dell e1505 (6400) laptop, and I am trying to get wide screen resolutions working. I followed a few different tutorials on getting it to work, but none worked. When I replaced the BIOS entry, the resolution that I replaced disapeared, but I couldn't use the one I replaced it with. I am using 6.10, and in the ubuntu wiki it says it should work "out-of-the-box" once I install 915resolution, but it doesn't. Any ideas?

---

### Post by linux_kid on 2007-02-24
Did you restart your pc after installing 915resolution? 
This is becuase it requires the X server to be restarted.

---

### Post by DiamondX on 2007-02-24
Yes, I restarted immediately after installing 915resolution, and it still didn't work.

---

### Post by Bram001 on 2007-02-25
I have the same problem.
My graphics controller is the Intel 82852/82855 GM/ME.
The X11org log says modes 50(640x480, 32bits), 52(800x600, 32bits) are supported(they have an asterisk) but not 54 with 1024x768. And that is the resolution I need.
the X11org log goes on with the message

"Not using mode "1024x768" (no mode of this name)"

and uses 800x600 even though only 1024x768 has been specified in the configuration.

When I use 915resolution to change the resolution of mod 50 nothing happens but when I change 52 that mode becomes unsupported and I only get 640x480.

---

### Post by dotman on 2007-03-07
Diamond,

What does your xorg.conf look like?
What does your 915resolution -l look like?
What is your desired resolution?

****EDIT****
Looked up that laptop, are you aiming for 1280x800?

---

### Post by piotrwoj on 2007-03-07
Hello! My english is very bad.
1) dpkg-reconfigure xserver-xorg, next, next, next....
2) Effect is my xorg config file:
#---------------------------------------------------
Section "Files" 
FontPath "/usr/share/X11/fonts/misc" 
FontPath "/usr/share/X11/fonts/cyrillic" 
FontPath "/usr/share/X11/fonts/100dpi/:unscaled" 
FontPath "/usr/share/X11/fonts/75dpi/:unscaled" 
FontPath "/usr/share/X11/fonts/Type1" 
FontPath "/usr/share/X11/fonts/100dpi" 
FontPath "/usr/share/X11/fonts/75dpi" 
FontPath "/usr/share/fonts/X11/misc" 
# path to defoma fonts 
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 
 
Section "Module" 
Load "bitmap" 
Load "dbe" 
Load "ddc" 
Load "dri" 
Load "extmod" 
Load "freetype" 
Load "glx" 
Load "int10" 
Load "record" 
Load "type1" 
Load "v4l" 
Load "vbe" 
SubSection "extmod" 
Option "omit xfree86-dga" # don't initialise the DGA extension 
EndSubSection 
EndSection 
 
Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "CoreKeyboard" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
Option "XkbLayout" "pl" 
Option "XkbOptions" "lv3:ralt_switch" 
EndSection 
 
Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
Option "CorePointer" 
Option "Device" "/dev/input/mice" 
Option "Protocol" "ExplorerPS/2" 
Option "ZAxisMapping" "4 5" 
EndSection 
 
Section "InputDevice" 
Identifier "Synaptics Touchpad" 
Driver "synaptics" 
Option "SendCoreEvents" "true" 
Option "Device" "/dev/psaux" 
Option "Protocol" "auto-dev" 
Option "HorizScrollDelta" "0" 
EndSection 
 
Section "InputDevice" 
Driver "wacom" 
Identifier "stylus" 
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event 
# for USB 
Option "Type" "stylus" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 
 
Section "InputDevice" 
Driver "wacom" 
Identifier "eraser" 
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event 
# for USB 
Option "Type" "eraser" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 
 
Section "InputDevice" 
Driver "wacom" 
Identifier "cursor" 
Option "Device" "/dev/wacom" # Change to 
# /dev/input/event 
# for USB 
Option "Type" "cursor" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 
 
Section "Device" 
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller" 
Driver "i810" 
VendorName "i915" 
BoardName "i810" 
Option "DRI" "true" 
VideoRam 131072 
Option "XAANoOffscreenPixmaps" "true" 
EndSection 
 
Section "Monitor" 
Identifier "Generic Monitor" 
Option "DPMS" 
HorizSync 28-64 
VertRefresh 43-60 
EndSection 
 
Section "Screen" 
Identifier "Default Screen" 
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller" 
Monitor "Generic Monitor" 
DefaultDepth 24 
SubSection "Display" 
Depth 24 
Modes "1280x800" 
EndSubSection 
EndSection 
 
Section "ServerLayout" 
Identifier "Default Layout" 
Screen "Default Screen" 
Option "AIGLX" "true" 
InputDevice "Generic Keyboard" 
InputDevice "Configured Mouse" 
InputDevice "stylus" "SendCoreEvents" 
InputDevice "cursor" "SendCoreEvents" 
InputDevice "eraser" "SendCoreEvents" 
InputDevice "Synaptics Touchpad" 
EndSection 
 
Section "DRI" 
Mode 0666 
EndSection 
Section "Extensions" 
Option "Composite" "Enable" 
Option "RENDER" "Enable" 
EndSection 
#-------------------------------------------------
This is work greet!
Piotrwoj I love ubuntu: [Drzwi Warszawa]("http://www.drzwi-warszawa.pl/") and [Drzwi Antyw&#322;amaniowe]("http://www.domar.biz.pl")

---

### Post by oicu on 2007-03-07
try changing /etc/default/915resolution file.

MODE=auto
XRESO=1024
YRESO=768
BIT=

---

### Post by DiamondX on 2007-03-07
> **dotman said:**
> Diamond,

What does your xorg.conf look like?
What does your 915resolution -l look like?
What is your desired resolution?

****EDIT****
Looked up that laptop, are you aiming for 1280x800?

Yea, 1280x800. Here is my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "XAANoOffscreenPixmaps" "true" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions" 
    Option "Composite" "true"
EndSection
```

I had ```
Option "ForceBIOS" "1024x768=1400x1050"
``` in there under Devices, but I got rid of that when it wasnt working.

915resolution -l is:
```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1280x800, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1280x800, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1280x800, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```
As you can see, I modified modes 3a, 4a, and 5a, but that also didnt work.

oicu: I tried that, but it also didnt work. I had it set to ```
MODE=auto
XRESO=1280
YRESO=800
BIT=
```

---

### Post by JohnPhys on 2007-03-26
Diamond,

If I'm not mistaken, you also need the 1280 x 800 mode to be listed in the xorg.conf.  I looks like the 915resolution stuff is set up ok.

If I had to guess, 915resolution is fine, X just can't switch to it since it's not listed in the xorg.conf

---

### Post by DiamondX on 2007-03-26
It works now, thanks. I just added "1280x800" to all of the modes, and now it works!

---

### Post by JohnPhys on 2007-03-27
Glad to hear it :)

---

