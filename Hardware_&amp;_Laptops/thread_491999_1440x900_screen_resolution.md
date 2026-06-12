---
title: "1440x900 screen resolution"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by mccord3576 on 2007-07-04
I have been trying to finish the install on my wife's laptop.  Pretty much the last thing I need to do is get the resolution set to 1440x900 which is what it was in Windows XP.  The laptop has an ATI Mobility Radeon 9600 M10 (from /var/log/Xorg.1.log) and since install it has defaulted to 1280x800.  Nothing that I have tried has been able to change the resolution.  I have installed the ATI proprietary driver through Adept Manager, and using the ATI installation program.

Using ddcprobe I get the following output:

vbe: VESA 2.0 detected.
oem: ATI MOBILITY RADEON 9600
memory: 65536kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

I don't see 1440x900 in here which makes me think that I may not be able to set it on the laptop.  It is also missing in the Xorg log file:

(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   83.47  1280 1344 1472 1680  800 801 807 831
(**) fglrx(0):  Default mode "1280x768": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   83.47  1280 1344 1472 1680  768 785 791 831
(**) fglrx(0):  Default mode "1024x768": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   83.47  1024 1216 1344 1680  768 786 792 831
(**) fglrx(0):  Default mode "848x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   83.47  848 1128 1256 1680  480 642 648 831
(**) fglrx(0):  Default mode "800x600": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   83.47  800 1104 1232 1680  600 702 708 831
(**) fglrx(0):  Default mode "720x576": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   83.47  720 1064 1192 1680  576 690 696 831
(**) fglrx(0):  Default mode "720x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   83.47  720 1064 1192 1680  480 642 648 831
(**) fglrx(0):  Default mode "640x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   83.47  640 1024 1152 1680  480 642 648 831
(**) fglrx(0):  Default mode "640x400": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   83.47  640 1024 1152 1680  400 602 608 831
(**) fglrx(0):  Default mode "640x350": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   83.47  640 1024 1152 1680  350 577 583 831
(**) fglrx(0):  Default mode "512x384": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   83.47  512 960 1088 1680  384 594 600 831
(**) fglrx(0):  Default mode "400x300": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   83.47  400 904 1032 1680  300 702 708 831 doublescan
(**) fglrx(0):  Default mode "320x240": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   83.47  320 864 992 1680  240 642 648 831 doublescan
(**) fglrx(0):  Default mode "320x200": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   83.47  320 864 992 1680  200 613 619 831 doublescan
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (81, 67)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   83.47  1280 1344 1472 1680  800 801 807 831
(**) fglrx(0):  Default mode "1280x768": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   83.47  1280 1344 1472 1680  768 785 791 831
(**) fglrx(0):  Default mode "1024x768": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   83.47  1024 1216 1344 1680  768 786 792 831
(**) fglrx(0):  Default mode "848x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   83.47  848 1128 1256 1680  480 642 648 831
(**) fglrx(0):  Default mode "800x600": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   83.47  800 1104 1232 1680  600 702 708 831
(**) fglrx(0):  Default mode "720x576": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   83.47  720 1064 1192 1680  576 690 696 831
(**) fglrx(0):  Default mode "720x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   83.47  720 1064 1192 1680  480 642 648 831
(**) fglrx(0):  Default mode "640x480": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   83.47  640 1024 1152 1680  480 642 648 831
(**) fglrx(0):  Default mode "640x400": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   83.47  640 1024 1152 1680  400 602 608 831
(**) fglrx(0):  Default mode "640x350": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   83.47  640 1024 1152 1680  350 577 583 831
(**) fglrx(0):  Default mode "512x384": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   83.47  512 960 1088 1680  384 594 600 831
(**) fglrx(0):  Default mode "400x300": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   83.47  400 904 1032 1680  300 702 708 831 doublescan
(**) fglrx(0):  Default mode "320x240": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   83.47  320 864 992 1680  240 642 648 831 doublescan
(**) fglrx(0):  Default mode "320x200": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   83.47  320 864 992 1680  200 613 619 831 doublescan

Any one know of anything else that I can try.  I will also post my xorg.conf just for good measure:


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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900" "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


Thanks

---

