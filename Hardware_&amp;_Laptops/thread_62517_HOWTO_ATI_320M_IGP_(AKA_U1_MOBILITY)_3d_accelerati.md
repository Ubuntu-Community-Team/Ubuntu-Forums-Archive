---
title: "HOWTO: ATI 320M IGP (AKA U1 MOBILITY) 3d acceleration!"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by Jeezis on 2005-09-05
ok, i'm running kubuntu 5.04 hoary on my hp pavilion ze4420us. it has an ati radeon 320m (u1 mobility). now, just because this worked for me i'm not going to guarantee it works for everyone.

first of all, you need to have the 'radeon' driver, not the 'ati' or 'fglrx' driver, those will not work. this IS NOT the ati proprietary driver! i believe this is included with ubuntu and kubuntu hoary, just select it when your configuring X. if you already did that, or don't know how to, it is pretty simple to edit the configuration file to make your display manager use this driver. 
first, get into console then type this:
```
~$sudo nano /etc/X11/xorg.conf
``` 
you should be in the nano console text editor and see a whole lot of text. don't be intimidated. scroll down to the "Graphics device section." regardless of what it says, you want it to say this:
```
# === ATI device section ===

Section "Device"
    Identifier                          "ATI Radeon U1"
    Driver                              "radeon"
    BusID                               "PCI:1:5:0"
    BoardName                           "Radeon Mobility U1"
    Option "AGPMode" "4"
    Option "ForcePCIMode" "True"
    Option "EnablePageFlip" "True"
```
press ctrl+x and hit "y" when it asks if you want to save, just press enter when it asks what you want to call the file.

that makes sure you are using the stock radeon driver, it supports 2d acceleration, but 3d is still run by software.

next, you need to go to: [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
you will need to download BOTH of the following files: [http://dri.freedesktop.org/snapshots/common-20050718-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050718-linux.i386.tar.bz2) 
AND
[http://dri.freedesktop.org/snapshots/radeon-20050718-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/radeon-20050718-linux.i386.tar.bz2)

make sure the numbers in the filenames match, otherwise they will be incompatible.

you'll want to unpack both of them, there should be a readme inside that tells you where the files should go.

you want to change to /usr/src/dripkg 
then simply type
```
~$sudo sh install.sh
``` 

what this does is start the dri package, it patches the radeon driver to use direct rendering. after it's done just reboot and you should have 3d acceleration!

to check, simply type:
```
`~$fglrxinfo
``` 

it should show something like this:
```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20050528 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.2 Mesa 6.3


```

hopefully that helps, i know it's not definitive, but it worked for me. reply with any problems and such and i'll see if i can help :)

GOOD LUCK!

---

### Post by byen on 2005-09-05
Good to know someone has got it working...working on it right now..will let you know!

EDIT: trying to find the destination folders for both...any sugg?

I tried doing that and i get this:

[COLOR=Red]Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted.[/COLOR]

now where do i begin? please help.

---

### Post by Jeezis on 2005-09-05
ok, first, do you have the build-essential package?

to get if/check if you do have it, type:
```
~$sudo apt-get install build-essential
```

gah, i'm sorry, i can't find where i unpacked them to. i'll keep searching. i knew i should have included it, but i've been so excited downloading and playing games like enemy territory and army ops that i forgot to properly document everything :(

---

### Post by Pikapooh on 2005-09-06
Tested on Hoary Ubuntu, Compaq Presario 2100

byen:

Kill X, unpack radeon package to ~/, then
cd ~/dripkg
./install.sh

Next delete ~/dripkg and unpack common package to ~/ and repeat
cd ~/dripkg
./install.sh

Restart X. U will need build-essential and linux-header packages, maybe some other too.


Jeezis, few questions:

Does Kubuntu use Xorg (just like Ubuntu) or XFree? I've heard that current DRI packages for Xorg are now maintained by Xorg, not dri.org.

Can u play games with decent speed? I'm wondering about

OpenGL renderer string: Mesa DRI...

Doesn't "Mesa" means that some kind of 'software OpenGL' is used instead hardware? I've only tried UT'99 and it looks kinda weird, so I'am not really sure if hardware acceleration is enabled. When I try to enable OpenGL acceleration in Java apps, it doesn't work, so I'm really doubtfull...

Can u post your full xorg.conf file and output from xdpyinfo, glxinfo and glxgears? Yeah, damn long, but I will be really happy ;-).

Anyway, m8, big thx. I was fighting with this f*** 320M for long time. Now I have at least direct rendering enabled :>

Cheers

---

### Post by Jeezis on 2005-09-07
kubuntu does use xorg. the dri module is technically for xfree86, but i figure what the heck and tried it and it worked! ok, heres the output you asked for:

xorg.conf
```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

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
    Driver	"kbd"
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
    Option "XkbModel"	"pc101"
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

    Driver      "vga"
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
    Identifier                          "ATI Radeon U1"
    Driver                              "radeon"
    BusID                               "PCI:1:5:0"
    BoardName                           "Radeon Mobility U1"
    Option "AGPMode" "4"
    Option "ForcePCIMode" "True"
    Option "EnablePageFlip" "True"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
#    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)" 
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
#    BusID "PCI:1:05:0"    # no device found at config time
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
    Device      "ATI Radeon U1"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
      # Option      "MonitorLayout" "LVDS, TMDS"
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

```
xdpyinfo:
```

name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    60802000
X.Org version: 6.8.2
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x1600005, revert to PointerRoot
number of extensions:    30
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    FontCache
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  print screen:    no
  dimensions:    1024x768 pixels (347x260 millimeters)
  resolution:    75x75 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x48
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa4031
    KeyPressMask             EnterWindowMask          LeaveWindowMask
    KeymapStateMask          StructureNotifyMask      SubstructureNotifyMask
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask
    ColormapChangeMask
  number of visuals:    16
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```
glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20050528 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.2 Mesa 6.3
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

hope that helps. all i know is that now i can play enemy territory and such no problem :)

---

### Post by Pikapooh on 2005-09-07
Heh, there is smth really weird with UT. When I start game everything is moving so fast, that it is unplayable - bots and my player are moving 5 times faster then on Windows :D. And it looks rather smooth, just damn fast. Strange thing is that when  I type 'timedemo 1' it shows 5-10 FPS :x. I will make some screenshots and compare to Windows version to see if there is hardware acceleration enabled...

If I find more time I will test some other 3D games...

And thx for xorg.conf etc content. I will compare with mine... at home, now I'm working hard :>

---

### Post by Jeezis on 2005-09-08
[QUOTE=Pikapooh]Heh, there is smth really weird with UT. When I start game everything is moving so fast, that it is unplayable - bots and my player are moving 5 times faster then on Windows :D. And it looks rather smooth, just damn fast. Strange thing is that when  I type 'timedemo 1' it shows 5-10 FPS :x. I will make some screenshots and compare to Windows version to see if there is hardware acceleration enabled...

If I find more time I will test some other 3D games...

And thx for xorg.conf etc content. I will compare with mine... at home, now I'm working hard :>[/QUOTE]
 hmm, i can't help you with ut, i don't have that game >_< i hope you figure it out though!

---

### Post by byen on 2005-09-09
hey guys.thanks for the reply...i tried doind what you said..but i keep getting this...

> Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
here is what my dri.log file says:
> Makefile:163: *** Cannot find a kernel config file.  Stop.


any suggestions?thanks.

---

### Post by Jeezis on 2005-09-09
hmm, that's awfully vague. i wish it told you what config file you where missing :-/

---

### Post by niobe_logos on 2005-09-14
I get a similar error when I try to install. In the dri.log file I get this:

make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/usr/src/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be
enabled in the kernel.  Stop.


Anybody have any clues as to what's going on? Where should I unpack the files? I have this idea the error's happening because things are in the wrong place to find files.  I've downloaded build-essential and the relevant headers....

Please help, any advice appreciated. I tried this because I've got a Toshiba Satellite A65, and I've read that these same drivers work fine under Gentoo.

---

### Post by ulovemikeroch on 2005-11-06
[QUOTE=byen]hey guys.thanks for the reply...i tried doind what you said..but i keep getting this...


here is what my dri.log file says:



any suggestions?thanks.[/QUOTE]
Ok, I'm having the exact same problem. And then I followed pikapoohs advice, and install all the linux headers drivers. I ran it, but I still can't install it. The same errors appear. What other packages am I missing? 

```
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2

```

---

### Post by ulovemikeroch on 2005-11-06
[QUOTE=ulovemikeroch]Ok, I'm having the exact same problem. And then I followed pikapoohs advice, and install all the linux headers drivers. I ran it, but I still can't install it. The same errors appear. What other packages am I missing? 

```
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/var/tmp/dripkg/radeon/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/var/tmp/dripkg/radeon/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/var/tmp/dripkg/radeon/dripkg/drm/linux-core'
make: *** [radeon.o] Error 2

```[/QUOTE]

Edit:I tried to see if Enemy territory would run without install gint eh 2nd driver. Turns out it does work. It got me happy. But then I thought, if it runs without it, how much better will it run with the 2nd driver? So, yeah, I still want the other driver to work so the graphics and the gameplay would be better then already before. So until then, I can still get ET to work, and I'll just keep playing this until someone fixes our driver problems.

---

### Post by daller on 2005-11-16
This is where I get stuck!

dri.log:

/home/oskar/downloads/radeon-20050718-linux.i386/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel. Stop.

...So is it possible to enable, without recompiling the kernel?

I'm running Breezy with Kernel 2.6.12-9

...But it bumped into some other problems before this!

Maybe it will help you installing these packages:

sudo apt-get install build-essential linux-headers-$(uname -r) gcc-3.4

---

### Post by ]Nbx*cmD[ on 2006-12-01
Hi all,

I've successfully configured direct rendering in a very easy way, take a look at my howto:

[http://ubuntuforums.org/showthread.php?t=310018&highlight=ati+320m](http://ubuntuforums.org/showthread.php?t=310018&highlight=ati+320m)

---

### Post by newsteadmission on 2007-03-29
> next, you need to go to: [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
you will need to download BOTH of the following files: [http://dri.freedesktop.org/snapshots/common-20050718-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20050718-linux.i386.tar.bz2) 
AND
[http://dri.freedesktop.org/snapshots/radeon-20050718-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/radeon-20050718-linux.i386.tar.bz2)

I was thrilled to see this after doing a search, finally a step by step guide. I then got to the part in the above quote and found the links were fried and dead. Now I am afraid to reboot or turn the system off because I have posted and saved all changes to just like you said in the previous steps. What shall I do?

---

