---
title: "Gutsy ATI card errors"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by switlikbob on 2007-12-27
Hi, I just installed a ATI card that I had laying around into my old Dell GX1 workstation b/c the onboard video was crappy.  I am unsure of what card model it is, but I followed the generic ati video card installation guide.  Here's my xorg.0.log file:

(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:01:00.0/rom: got 0KB
(EE) VESA(0): Cannot read V_BIOS (3)
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
bob@neary:/var/log$ tail -100 Xorg.0.log
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 02:0b:0
(WW) VESA: No matching Device section for instance (BusID PCI:2:11:0) found
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff001000 - 0xff00107f (0x80) MX[B]
        [5] -1  0       0xff000000 - 0xff000fff (0x1000) MX[B]
        [6] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [7] -1  0       0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
        [8] -1  0       0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [10] -1 0       0xfcfff000 - 0xfcffffff (0x1000) MX[B](B)
        [11] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [14] -1 0       0x0000cc00 - 0x0000cc7f (0x80) IX[B]
        [15] -1 0       0x0000cce0 - 0x0000ccff (0x20) IX[B]
        [16] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
        [18] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [19] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff001000 - 0xff00107f (0x80) MX[B]
        [5] -1  0       0xff000000 - 0xff000fff (0x1000) MX[B]
        [6] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [7] -1  0       0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
        [8] -1  0       0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [10] -1 0       0xfcfff000 - 0xfcffffff (0x1000) MX[B](B)
        [11] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000cc00 - 0x0000cc7f (0x80) IX[B]
        [18] -1 0       0x0000cce0 - 0x0000ccff (0x20) IX[B]
        [19] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [20] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
        [21] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [22] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
        [23] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [24] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:01:00.0/rom: got 0KB
(EE) VESA(0): Cannot read V_BIOS (3)
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
_________________
_________________

Any ideas?  It looks to me like th eOS is trying to load the onboard card and not the ATI PCI card?

---

### Post by switlikbob on 2007-12-27
And here is my /etc/X11/xorg.conf file:


# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.
# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#
# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************
# **********************************************************************
# DRI Section
# **********************************************************************
# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************
# **********************************************************************
# Server flags section.
# **********************************************************************
# **********************************************************************
# Input devices
# **********************************************************************
# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************
# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************
# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
# **********************************************************************
# Monitor section
# **********************************************************************
# Any number of monitor sections may be present
# **********************************************************************
# Graphics device section
# **********************************************************************
# Any number of graphics device sections may be present
# Standard VGA Device:
# === ATI device section ===
# **********************************************************************
# Screen sections
# **********************************************************************
# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
# **********************************************************************
# ServerLayout sections.
# **********************************************************************
# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.
### EOF ###

Section "ServerLayout"

# The Identifier line must be present
# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.
# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".
	Identifier     "Server Layout"
	Screen         "Screen0" 0 0
	Screen         "aticonfig-Screen[1]" Above "Screen0"
	InputDevice    "Mouse1" "CorePointer"
	InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
# The module search path.  The default path is shown here.
#    ModulePath "/usr/X11R6/lib/modules"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"

# This loads the DBE extension module.
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
# This loads the Type1 and FreeType font modules
	Load  "dbe"  	# Double buffer extension
	Load  "extmod"
#      Option    "omit xfree86-dga" 
	Load  "type1"
	Load  "freetype"
# This loads the GLX module
	Load  "glx"   # libglx.a
	Load  "dri"   # libdri.a
EndSection

Section "InputDevice"

# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.
#    Option "Protocol"   "Xqueue"
#    Option "Xleds"      "1 2 3"
#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"
# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"
# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""
#    Option "XkbDisable"
	Identifier  "Keyboard1"
	Driver      "kbd"
	Option	    "AutoRepeat" "500 30"
# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
	Option	    "XkbRules" "xfree86"
	Option	    "XkbModel" "pc101"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"

# Identifier and driver
# the following line.
#    Option "Protocol"   "Xqueue"
# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.
#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"
# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Device" "/dev/input/mice"
# When using XQUEUE, comment out the above two lines, and uncomment
	Option	    "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"
# ChordMiddle is an option for some 3-button Logitech mice
#    Option "ChordMiddle"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.
#    Chipset     "generic"
# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.
#    BusID       "PCI:0:10:0"
#    VideoRam    256
#    Clocks      25.2 28.3
	Identifier  "Standard VGA"
	Driver      "vga"
	VendorName  "Unknown"
	BoardName   "Unknown"
EndSection

Section "Device"

# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    # vendor=1002, device=5960
	Identifier  "ATI Graphics Adapter"
	Driver      "fglrx"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
# === misc DRI settings ===
	Option	    "mtrr" "off" # disable DRI mtrr mapper, driver has its own code for mtrr
	Option	    "DesktopSetup" "0x00000000"
	Option	    "MonitorLayout" "AUTO, AUTO"
	Option	    "IgnoreEDID" "off"
	Option	    "HSync2" "unspecified"
	Option	    "VRefresh2" "unspecified"
	Option	    "ScreenOverlap" "0"
# === TV-out Management ===
	Option	    "NoTV" "yes"
	Option	    "TVStandard" "NTSC-M"
	Option	    "TVHSizeAdj" "0"
	Option	    "TVVSizeAdj" "0"
	Option	    "TVHPosAdj" "0"
	Option	    "TVVPosAdj" "0"
	Option	    "TVHStartAdj" "0"
	Option	    "TVColorAdj" "0"
	Option	    "GammaCorrectionI" "0x00000000"
	Option	    "GammaCorrectionII" "0x00000000"
# === OpenGL specific profiles/settings ===
	Option	    "Capabilities" "0x00000000"
# === Video Overlay for the Xv extension ===
	Option	    "VideoOverlay" "on"
# === OpenGL Overlay ===
	Option	    "OpenGLOverlay" "off"
# === Center Mode (Laptops only) ===
	Option	    "CenterMode" "off"
# === Pseudo Color Visuals (8-bit visuals) ===
	Option	    "PseudoColorVisuals" "off"
# === QBS Management ===
	Option	    "Stereo" "off"
	Option	    "StereoSyncEnable" "1"
# === FSAA Management ===
	Option	    "FSAAEnable" "no"
	Option	    "FSAAScale" "1"
	Option	    "FSAADisableGamma" "no"
	Option	    "FSAACustomizeMSPos" "no"
	Option	    "FSAAMSPosX0" "0.000000"
	Option	    "FSAAMSPosY0" "0.000000"
	Option	    "FSAAMSPosX1" "0.000000"
	Option	    "FSAAMSPosY1" "0.000000"
	Option	    "FSAAMSPosX2" "0.000000"
	Option	    "FSAAMSPosY2" "0.000000"
	Option	    "FSAAMSPosX3" "0.000000"
	Option	    "FSAAMSPosY3" "0.000000"
	Option	    "FSAAMSPosX4" "0.000000"
	Option	    "FSAAMSPosY4" "0.000000"
	Option	    "FSAAMSPosX5" "0.000000"
	Option	    "FSAAMSPosY5" "0.000000"
# === Misc Options ===
	Option	    "UseFastTLS" "0"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "UseInternalAGPGART" "yes"
	Option	    "ForceGenericCPU" "no"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"

    #Option "backingstore"
	Identifier "Screen0"
	Device     "ATI Graphics Adapter"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"

# Access to OpenGL ICD is allowed for all users:
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
	Mode         0666
EndSection

---

### Post by Yellow Pasque on 2007-12-27
That is one messy xorg.conf, but the problem lies here:

from the log:
> (II) Primary Device is: PCI 02:0b:0
(WW) VESA: No matching Device section for instance (BusID PCI:2:11:0) found

from your xorg.conf "Device" section:
> BusID "PCI:1:0:0"

It looks like you need to change the BusID's to :2:11:0

---

### Post by terminal on 2007-12-27
go to terminal ( press ctrl-alt-f1 or boot in recovery mode ) . type "dpkg-reconfigure xserver-xorg" and follow intructions . Select radeon from driver list it provides you , since ur card is little old it should run well with open source radeon driver .

---

### Post by switlikbob on 2007-12-28
I ran a pci scan and found that the PCI ATI video card I have is called:

ATI RV280 Radeon 9200 Pro on bus 2:11:0

I tied changing the BUS id's, but that does me no good.  I re-ran the "dpkg-reconfigure xserver-xorg" after deleteing the "messy" xorg.conf file, and I changed the BUS ID to 2:11:0.  It now appears that the OS is loading the drivers for the onboard ATI 3D Rage Pro instead of the Radeon PCI card, but I do get an X display and gnome loads.  The problem is that the display is all screwed up.  I am thinking that I need to somehow reload the Radeon driver.  Should I remove all references to the Rage Pro onboard device?

---

### Post by switlikbob on 2007-12-28
Here's my new xorg.conf file (the relevant part):

Section "Device"
        Identifier      "ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "radeon"
        BusID           "PCI:2:11:0"
EndSection
Section "Monitor"
        Identifier      "DELL 1702FP"
        Option          "DPMS"
        HorizSync       31-80
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Monitor         "DELL 1702FP"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
_______________________________________
_______________________________________

The display is still all screwed up though.  Here's my /var/log/Xorg.0.log:

(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) AIGLX: Suspending AIGLX clients for VT switch
disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() :
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf0a80000 at 0xb7ada000
_________________________
_________________________

Any ideas?

---

### Post by Yellow Pasque on 2007-12-28
No, you don't need to remove the Rage device, as you're not using it (you're using the "Default Screen", which uses the 9200's Device section).

Is this your entire Xorg.0.log?

If you're trying to use DVI, this might be relevant:
[https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)

---

