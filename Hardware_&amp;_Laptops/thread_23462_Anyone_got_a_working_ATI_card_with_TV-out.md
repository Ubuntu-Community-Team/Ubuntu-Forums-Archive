---
title: "Anyone got a working ATI card with TV-out?"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by Michael_Grosberg on 2005-04-02
Yeah Yeah, I already opened a thread about it, but didn't get any useful replies, so here's another attempt:

Does anyone here have an ATI card with a working TV-out?
If you hav an ATI card and the TV-out isn't working for you, or if it can't work at all and it's a known issue, I'd like to know as well, so I know I'm not the only one.
If it is working, how does one get it to work?
What driver is used and what is the procedure to install it?

here's the instructions i've been trying to follow:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 

Here's the thread where I described the actuall effect of that attempt:
[http://www.ubuntuforums.org/showthread.php?t=23289](http://www.ubuntuforums.org/showthread.php?t=23289)

---

### Post by emuman on 2005-04-02
Here is my xorg.conf with dual head. First screen is a TFT, second TV.
The important part is 

Option "MonitorLayout"              "TMDS, STV"

and

the section "ServerLayout".

You may use my config as startpoint or create your own with fglrxconfig.

[FONT=System]
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

    Load        "dbe"   # Double buffer extension

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

    RgbPath     "/usr/X11R6/lib/X11/rgb"

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
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
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

    Identifier  "Keyboard1"
    Driver      "kbd"
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

    Option "XkbRules"   "xfree86"
    Option "XkbModel"   "pc105"
    Option "XkbLayout"  "de"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
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

#    Option "Emulate3Buttons"
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
    HorizSync   31.5
    VertRefresh 20 - 60
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier  "Monitor1"
    HorizSync   31.5
    VertRefresh 20 - 60
    Option "DPMS"
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
    Identifier                          "ATI Graphics Adapter connector 0"
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
    Option "DesktopSetup"               "0x00000000"
    Option "MonitorLayout"              "TMDS, STV"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "31.5       "
    Option "VRefresh2"                  "20 - 60"
    Option "ScreenOverlap"              "0"
# === TV-out Management ===
    Option "NoTV"                       "no"
    Option "TVStandard"                 "PAL-G"
    Option "TVHSizeAdj"                 "0"
    Option "TVVSizeAdj"                 "0"
    Option "TVHPosAdj"                  "0"
    Option "TVVPosAdj"                  "0"
    Option "TVHStartAdj"                "0"
    Option "TVColorAdj"                 "0"
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
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
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:2:0:0"    # vendor=1002, device=4e44
    Screen 0
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 1"
    Driver                              "fglrx"
    BusID "PCI:2:0:0"    # vendor=1002, device=4e44
    Screen 1
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
    Device      "ATI Graphics Adapter connector 0"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter connector 1"
    Monitor     "Monitor1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "640x480"
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
    Screen "Screen1" LeftOf "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###
[/FONT]

---

### Post by panabar on 2005-04-03
I have a desktop computer with radeon 9600 pro and my tv out is working properly.

These are the things I have done to get it working
install  xorg-driver-fglrx and fglrx-control
reboot the computer while the tv is connected ( and I saw the booting process on tv)
when gdm comes up tv out is cut. so I login and start fglrxcontrol to enable tv-out and configure setup.

This is all for radeon 9600 pro, but my laptop with radeon mobility 7500 do not have working tv out. :(

---

### Post by Michael_Grosberg on 2005-04-04
Thanks to anyone who helped me so far. I'm making some headway...
I used fglrxconfig to configure my driver, and I can now see it on my TV, but I still have some issues:

first of all, I tried using clone instead of dual head... maybe a mistake but for my purpose which is seing movies on my TV I felt it was the best.
It's supposed to work by copying the image you see on the monitor but scaling it down to fit the TV's resolution. Now, what actually happened was that I had a 1152X864 resolution on my monitor and a 640X480 with a virtual 1152X864 desktop on my TV, so I didn't see the whole desktop at once on my TV.
How do I set it up so I see the whole desktop on my TV while on the monitor it is still in the size I want - 1152X864?

I'll try and figure it out when I get back home, maybe I'll just reconfigure it using dual-head insted of clone.

The more serious problem was that I didn't see the movie being played.
I suppose it's something similar to Window's accelerated directDraw overlay which has to be disabled to show movies in screenshots or cloned displays, but how do I do that on linux? Obviously there's no DirectDraw...

Another issue is driver version, ATI has a newer driver on their website - 8.10.19, while the driver in the Ubuntu repository is 8.8.25.
I first tried installing the 8.8.25 and couldn't find how to configure it. I also installed fglrx-control, but couldn't find out how to run it, no application menu item was added and typing "fglrx-control" on the terminal didn't do anything.  I reverted to the ATI driver, read some more about the issue, and found out about fglrxconfig. I then installed 8.10.19 from ATI, but it seems fglrx-control is dependent on the older driver being installed. 
So, what driver are you using? can the new one be used with the control panel somehow? and how do you get to the control panel, anyhow?

Last issue - In about 50% of the times I try to log in, after I pass the login screen, all I get is a brown background and a working mouse pointer, but nothing more. No desktop, no Gnome/Ubuntu  splash screen.
I'm suspecting it has something to do with the driver because It started happening after I changed from ATI to FGLRX. Is there a log somewhere that I can check?

I'd appreciate any and all help in this.

---

### Post by philipacamaniac on 2005-04-15
[QUOTE=Michael_Grosberg]I also installed fglrx-control, but couldn't find out how to run it, no application menu item was added and typing "fglrx-control" on the terminal didn't do anything.  I reverted to the ATI driver, read some more about the issue, and found out about fglrxconfig. I then installed 8.10.19 from ATI, but it seems fglrx-control is dependent on the older driver being installed. 
[/QUOTE]

The FireGL control panel is added to the menu in Kubuntu. I think (I'm not on my Kubuntu box) the command is /usr/bin/fireglcontrol.

---

### Post by MWAAAHAAA on 2005-04-15
If you just want to watch movies, you really dont need to set up anything. You just plug in the cable connecting your tv to your card and it should give you proper tv output immediately as long as you stay out of graphical mode. Then if you want to play an mpeg or similar, usr mplayer with the vesa driver, e.g.:

mplayer -vo vesa muha.mpeg

or

mplayer -vo vesa:vidix muha.mpeg

You probably need admin privileges for this to work though, so forget about it if that's inacceptable for you.

---

