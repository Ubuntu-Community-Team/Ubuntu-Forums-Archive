---
title: "ATI Video card help!"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Granji on 2005-09-10
The ATI control panel, or the Ubuntu device don't pick up my video card type, they only list it as being ATI technologies, i've run through the GUI installer, and the fglrxconfig in terminal multiple times, and have gone through 3 X server breaks in the last 2 hours, I'm getting tired of installing/re-installing things to get this to pick up...and the other problem I'm having is with my GLX none of the 3D accelerated programs will run, besides glxgears, when I run fgl_glxgears I get an error stating Error: couldn't get fbconfig
... can anyone tell me what that means. I'm fairly new at linux, Ubuntu was recommended by a friend of mine, I like it, but I just a have few problems like this to clear up...The other one being, how do I get my webcam to work, it shows up when I plug it in, but what application would I use to grab images from it?

---

### Post by mlomker on 2005-09-10
You'll should do a search on ATI.  Questions about the driver get asked, literally, every day

If you type **fglrxinfo** at a prompt does it tell you it's using the MESA driver or does it give you ATI information?  That's the first thing to figure out--is the driver even loading.

Try **dmesg | grep fglrx** and you'll get the kernel info from when the module loads.  If it's not loading then that's problem #1.

Second, try creating an [xorg.conf](http://www.objorkum.com/scripts/fglrxconfig/) file from that website.  It's a lot cleaner and easier to look through than the command-line version.

---

### Post by Granji on 2005-09-10
Output from fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

Output from dmesg | grep fglrx

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 5631 using kernel context 0

---

### Post by Granji on 2005-09-11
Bump...help...somebody, i've been trying all day, and most of the night with no success. Oh, and I'm using the XF86Config-4 file, not a xorg.conf file...if that matters at all.

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]Bump...help...somebody, i've been trying all day, and most of the night with no success. Oh, and I'm using the XF86Config-4 file, not a xorg.conf file...if that matters at all.[/QUOTE]

It matters a great deal--Ubuntu reads the xorg.conf file.  If you used fglrxconfig to create the file then you need to rename it xorg.conf.  You shouldn't be seeing anything about MESA when the proper driver is loaded.

I'd recommend using the website that I pointed you at.  Back up your current xorg.conf and then cut/paste the output from that website into the file and save it.

I'm not sure what that error line means, exactly, but errors are never a good sign.  Give it a try, anyway.  If something goes wrong then your graphical session will fail to start and you'll need to copy your backup copy back to xorg.conf and keep troubleshooting.  If it's any consolation, I also spend an entire day getting mine to work...

---

### Post by Granji on 2005-09-11
hmmm, I've renamed the file, I've used the website you gave me, still with no luck, i'm looking for the ATI drivers/information on the HD but I can't find it anywhere, I was thinkin that maybe a clean install might solve the problem. GLX gears runs fine infact I have a fairly high fps

1337 frames in 5.0 seconds = 267.400 FPS
1243 frames in 5.0 seconds = 248.600 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1243 frames in 5.0 seconds = 248.600 FPS

Not the greatest, but it's pretty good by my standards. I tried to us fgl_glxgears, but it comes back with **Error: couldn't get fbconfig** i dont' know if I'm doing something wrong, oh, I dunno if I mentioned it before, but i'm using the ATI Radeon 9550 256mb DDR card.

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]but i'm using the ATI Radeon 9550 256mb DDR card.[/QUOTE]

I have a 9700 Pro and I get around 2000 fps.  You're obviously still running the MESA driver.

Why don't you repost the output of **fglrxinfo** and the driver section of your xorg.conf file.

Are you using the driver that came with Hoary or did you download the driver from ATI's website?  The Hoary one didn't work for me at all.

What I did:

[Download driver from ATI in RPM format.](http://www2.ati.com/drivers/linux/fglrx_4_3_0-8.16.20-1.i386.rpm) 

Open a terminal prompt in the directory that you downloaded the file to:

[b]
su
apt-get install alien
alien -D fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh
[/b]

If the module build completes successfully then your xorg.conf file should work.

---

### Post by Granji on 2005-09-11
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4


Yes still using MESA, and I did download the 8.16.20 drivers from ATI, and used their gui installer.

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "fglrx"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "single" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "1"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:1:0:0"    # vendor=1002, device=4153
    Screen 0
EndSection

Is that what you were looking for?

---

### Post by Granji on 2005-09-11
I have an error running the **sh make.sh** from your steps The error is

[B]ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h[/B]

---

### Post by mlomker on 2005-09-11
You need to have the kernel headers installed for your kernel. 

From a terminal prompt:

[b]
uname -r
[/b]

Go into synaptic and search for linux-headers and install the ones with the numbers that match from the output of the above command.

---

### Post by Granji on 2005-09-11
Okay, I installed the headers, and the module build worked, and I did the **sh make_install.sh** but to avail, MESA drivers are still loading. Maybe the ati drivers didn't install correctly because I didn't run the install with **--force-overwrite**, so they didn't overwrite the **MESA** drivers.

---

### Post by mlomker on 2005-09-11
I'm assuming that you rebooted to load the new fglrx driver.

Please post the contents of:

xorg.conf file
dmesg | grep fglrx

---

### Post by Granji on 2005-09-11
# File: XF86Config-4
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

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
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"Keyboard"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
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

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


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

Section "Monitor"
    Identifier  "Monitor0"
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


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "fglrx"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "single" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "1"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:1:0:0"    # vendor=1002, device=4153
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

Thats it. from beginning to end. Thanks for your time, I know this must be frustrating you as much as it is me. For the ** dmesg | grep fglrx ** it doesn't do anything, just skips a line and brings back the command line

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]For the  dmesg | grep fglrx  it doesn't do anything, just skips a line and brings back the command line[/QUOTE]

Oh?  Do you see the fglrx driver listed in /etc/modules?  If not, add it in there and restart.

---

### Post by Granji on 2005-09-11
The only thing that gets me, is that at the top of the file contents, it says...although commented it say ** file: XF86Config-4 ** should I delete that file, and see if it helps? I of course would back it up incase it breaks X. how would I add it in there..just add a line with flgrx in it?

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

Those are my current contents

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]The only thing that gets me, is that at the top of the file contents, it says...although commented it say ** file: XF86Config-4 ** should I delete that file, and see if it helps? I of course would back it up incase it breaks X.[/QUOTE]

That's what the file is called on other distributions.  In Ubuntu that file has to be named xorg.conf.

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]Those are my current contents[/QUOTE]

Add fglrx at the bottom.

---

### Post by Granji on 2005-09-11
Added, and rebooted, still get the same MESA output from fglrxinfo...how would I completely uninstall the ATI drivers and start over again?

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]Added, and rebooted, still get the same MESA output from fglrxinfo...how would I completely uninstall the ATI drivers and start over again?[/QUOTE]

Go into Synaptic and search on fglrx and remove the package that we just installed using the 'complete removal' option.

Go to a terminal prompt:

[b]
su 
updatedb
locate fglrx | more
[/b]

Delete everything that locate command finds.

Did you re-run **dmesg | grep fglrx** to verify that the module loaded?

---

### Post by Granji on 2005-09-11
[fglrx:firegl_unlock] *ERROR* Process 5988 using kernel context 0

Thats what I get when I run ** dmesg | grep fglrx **

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji][fglrx:firegl_unlock] *ERROR* Process 5988 using kernel context 0
[/QUOTE]

That's the core problem, right there.  I Googled that error and it suggests updating to the latest driver, which you just tried.  I recommend that you proceed with deleting everything related to fglrx and then reinstalling that *.deb file.  You were heading down that path already, so I think that's a good decision.

If the error persists after you re-do everything then you might want to jump on the [ATI forums](http://www.rage3d.com/board/) with that error message and get some feedback.

---

### Post by Granji on 2005-09-11
Okay, straight up n00b question I do all my super user stuff through terminal, and have yet to figure out the equivalent of delete :S

Is there an easier to do this, than 1 file at a time?

---

### Post by mlomker on 2005-09-11
**rm -fr /whatever/dir** to delete an entire directory (be very careful, needless to say).

---

### Post by Granji on 2005-09-11
Is it safe to delete the fglrx files in the **/var/lib/dpkg/info ** directory?

---

### Post by mlomker on 2005-09-11
[QUOTE=Granji]Is it safe to delete the fglrx files in the **/var/lib/dpkg/info ** directory?[/QUOTE]

Yes, but it shouldn't matter.  That's just info about previously installed packages (the .deb files).

---

### Post by Granji on 2005-09-11
okay...all the fglrx related stuff is gone, gonna start over again, should I start with the debian package, or the Hoary 5.04 specific ATI installer?

---

### Post by mlomker on 2005-09-11
I only had luck with the .deb package, personally.  It's totally your call.

---

### Post by Granji on 2005-09-11
Finally..after all that work, learned a lot though, so thats an upside to it all. the .deb package worked, and I have 3d Acceleration with the proper output from fglrxinfo, Thanks a ton mlomker!!   :-)  :-)  :-)  :grin:  :grin:  :grin:

---

### Post by mlomker on 2005-09-11
Awesome!  I'm curious...what is your fps rate in glxgears?

---

### Post by Granji on 2005-09-11
8517 frames in 5.0 seconds = 1703.400 FPS
10040 frames in 5.0 seconds = 2008.000 FPS
10038 frames in 5.0 seconds = 2007.600 FPS
10040 frames in 5.0 seconds = 2008.000 FPS

Thats the average

---

### Post by Cashel on 2005-09-11
If you have DSL (or dont mind some realy long downloads for packages you dont have) you might go ahead and give this rather excellent howto and installer a try:

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

It's not for the faint of heart (and you may need to comment out the control panel bits in the "rules" file since the new version of ATI's proprietary driver doesnt have the same files) .... 

It did a world of good for me... 

Good luck! :!:

---

### Post by Thulemanden on 2005-09-13
I have an ATI AIW 128 and get only app. 800 fps in glxgears.
How can I improve on that please, if I should?

Section "Device"
 Identifier "ATI Technologies, Inc. Radeon 7200 (R100 QD)"
 Driver  "ati"
 BusID  "PCI:1:0:0"
EndSection

Section "Monitor"
 Identifier "Standard Sk&#65533;m"
 Option  "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection

---

### Post by mlomker on 2005-09-13
Follow the instructions in this thread to upgrade to the fglrx driver.  The ATI driver is generic and although that's better than MESA, it isn't all that fast.

---

### Post by awseft on 2006-09-09
When I try to dpkg I get this:

awseft@awseft:~/Desktop$ sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
(Reading database ... 93385 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.16.20-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.16.20-2_i386.deb (--install):
trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-control
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
fglrx-4-3-0_8.16.20-2_i386.deb
awseft@awseft:~/Desktop$

---

### Post by awseft on 2006-09-09
Help :(

---

### Post by awseft on 2006-09-09
Restarted and nothing

Here's what I did:
su
apt-get install alien
alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh

When I try to dpkg I get this:
awseft@awseft:~/Desktop$ sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
(Reading database ... 93385 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.16.20-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.16.20-2_i386.deb (--install):
trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-control
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
fglrx-4-3-0_8.16.20-2_i386.deb
awseft@awseft:~/Desktop$

But my xorg.conf does say:
Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

But the resolution is off and the ATI controller says:

Driver does not provide the FireGL X11 extenstions!
Panel components will operate only partially.

---

