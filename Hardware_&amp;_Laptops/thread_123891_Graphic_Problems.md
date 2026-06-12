---
title: "Graphic Problems"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by Xenodwarf on 2006-01-31
Hi. I've got a HP Pavilion ce2310 with a ATI RADEON XPRESS 200M

I installed ubuntu last night and everyhing went just fine until i rebooted for the last time and the computer tried to start X.
I got an error message that said it couldent start X because of some configuration problems. I managed to start it but the screen went in to a flickering caos of horisontal and vertical lines.

Does anyone know whats causing this, and how to fix it?

mind that I have very little experience with linux.

Thanks
Xeno

---

### Post by stangbang on 2006-01-31
check your xorg.conf file and see what driver it is using for video. You might also try not booting into x and typing "sudo dpkg-reconfigure -phigh xserver-xorg" without the quotes. This will guide you through reconfiguring the xorg.conf file. Try using both the ati driver, and the fglrx driver. You may need to dowload the fglrx driver with apt-get. the package is "xorg-driver-fglrx"

---

### Post by Xenodwarf on 2006-02-01
Thanx for the reply. I'll give it a try.

---

### Post by zachtib on 2006-02-01
[QUOTE=Xenodwarf]Hi. I've got a HP Pavilion ce2310 with a ATI RADEON XPRESS 200M[/QUOTE]

I pity you.

The radeon xpress is known to have terrible linux support, the following got my friends compaq with the same symptoms working.

after doing the dpkg-reconfigure, edit your xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```

scroll down to your device section, and add or modify a line, so it looks like this:

```
Option "RenderAccel" "false"
```

then reboot

---

### Post by Xenodwarf on 2006-02-01
Non of the above solved my problem.. No changes at all..

---

### Post by zachtib on 2006-02-01
ok, run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then post your xorg.conf file here
its at /etc/X11/xorg.conf

---

### Post by klett on 2006-02-01
Hi,

I'm not a native speaker, but I'll do my best.
I had the same problem a month ago, but I got it running in the end. Here's what I did:

First, run
[B]sudo apt-get install xorg-fglrx-driver
[/B]
and then

**sudo fglrxconfig** 

I accepted most default settings, but I did choose the correct keyboard, which I had found out with the dpkg-reconfigure xorg-xserver. I think I didn't choose the default settings for the mouse either. 

After that you can either reboot or run startx. 
If you run startx,  it won't work after rebooting and logging as a normal user :twisted: .The reason is that startx has set the root as the owner of the /home/your_user_name/.ICEauthority file.

A way to solve this problem is to log in in text mode, remove that file and reboot. The file with the correct owner will be automatically generated during the booting process.

This will provide you with a graphics interface. However, you'll notice that it doesn't work as it should, especially when the computer is shutting down. The reason is that this driver doesn't support this graphic card. I downloaded the correct driver from the ati website and that problem disappeared. But the  3D animations run slowlier than they did with the previous driver.:-k

---

### Post by Xenodwarf on 2006-02-02
Thanks guys, you are really being helpfull.

I will give this a shot when i get home from work. 
There is just one thing, im not sure how to get the xorg.conf file here, seing that im not connected to the internet while in linux.
I guess its possible to copy it to my windows partition, but i don't know how to do that.

---

### Post by stangbang on 2006-02-02
the xorg.conf file is located here:

/etc/X11/xorg.conf

just open it with vi or kate or whatever text editor you prefer to use. (note that you need super user rights to make changes so you may need to use sudo)

if you have a fat32 partition you should be able to go to /media and see a list of available drives and have it work. If you only got your linux partition and a NTFS partition you can install the ntfs tools that allow you to access an ntfs partition, but I would not suggest writing to it from linux.

---

### Post by zachtib on 2006-02-02
[QUOTE=Xenodwarf]Thanks guys, you are really being helpfull.

I will give this a shot when i get home from work. 
There is just one thing, im not sure how to get the xorg.conf file here, seing that im not connected to the internet while in linux.
I guess its possible to copy it to my windows partition, but i don't know how to do that.[/QUOTE]

Ooh, thats a good question.  I would suggest copying it to a pendrive if you have one.  Otherwise, im not sure how you're going to get it up here

---

### Post by Xenodwarf on 2006-02-02
Yea, and thats like a USB memorystick right?
will that work in linux without any problems?

I tried "sudo apt-get install xorg-fglrx-driver"
But i only get a message saying it cant find the package.

---

### Post by stangbang on 2006-02-02
You probably have not added the universe repository to your sources.list. open up the terminal and type sudo vi /etc/apt/sources.list press i to be able to edit. scroll down till you see

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

Remove the # from infront of deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe, and deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe.

after doing that press esc then :wq and press enter.

You will now be back at the terminal. update the apt list with

sudo apt-get update

then try to install the fglrx driver again. It is part of the universe repository so you probably just have the defaults in your sources.list.

As for the pen drive yes that is just a usb memory stick, and ubuntu should have support for that built in.

---

### Post by mscman on 2006-02-02
[QUOTE=Xenodwarf]Yea, and thats like a USB memorystick right?
will that work in linux without any problems?

I tried "sudo apt-get install xorg-fglrx-driver"
But i only get a message saying it cant find the package.[/QUOTE]

Apt-get won't work at all since you don't have an internet connection when you're working in linux.  You might try using the generic VESA in xorg if you haven't already, that worked on my friend's computer.  Sorry I can't be of more help!

---

### Post by Xenodwarf on 2006-02-02
[QUOTE=mscman]Apt-get won't work at all since you don't have an internet connection when you're working in linux.  You might try using the generic VESA in xorg if you haven't already, that worked on my friend's computer.  Sorry I can't be of more help![/QUOTE]

Do i just change the name of the driver in xorg.conf from ATI to VESA ?

---

### Post by stangbang on 2006-02-02
yes just replace ati with vesa.

also since you dont have an internet connection you can goto [http://packages.ubuntu.com](http://packages.ubuntu.com) and download any of the packages you need, and then install them using dpkg. Do you not have any internet, or are you just not able to access it with ubuntu?


to use dpkg open the terminal and goto the directory with the packages.

type: dpkg --install packagename

install the dependancys first. These will be listed with the package when you goto [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Xenodwarf on 2006-02-02
I do have an internetconnection i just cant connect from linux yet.
The problem is i dont know how to get the packages from my windows partition to the linux partition.

---

### Post by stangbang on 2006-02-02
I am assuming your windows partition is NTFS. You have a few choices. 
choice 1 - use a floppy disk or a thumb drive to transfer the ntfsprogs package
( [http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs](http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs) )
Choice 2 - If you have a swap partition you can delete it, and turn it into a fat 32 partition and access it with both linux and windows. then after copying the files over return it back to a swap partition.

If your windows partition is already a fat32 partition you can already access it by going to
/media
here is where all your different drives and partitions are located.

Also is this wireless that is not working, or are you not able to connect with wired?

---

### Post by klett on 2006-02-02
My laptop is an HP Pavilion ze2000 series too, and my USB ports worked out of the box. By the way, I tried the Vesa driver and it worked, although I think the ati one is better.

However, if you configured your internet connection during installation process, you should be able to connect with your ethernet card. Anyway, you'll face the problem of your internet connection sooner or later, so I think It's worth giving it a try and configure it.

---

### Post by Xenodwarf on 2006-02-03
[QUOTE=klett]My laptop is an HP Pavilion ze2000 series too, and my USB ports worked out of the box. By the way, I tried the Vesa driver and it worked, although I think the ati one is better.

However, if you configured your internet connection during installation process, you should be able to connect with your ethernet card. Anyway, you'll face the problem of your internet connection sooner or later, so I think It's worth giving it a try and configure it.[/QUOTE]

Do you have the same display adapter as i have? 
thats wierd, im starting to think that im doing something very wrong when trying to configure xorg.conf

Is there any way i can access the linux drive from windows and just snag xorg.conf from there?

---

### Post by klett on 2006-02-03
Hi Xenodwarf,

I forgot to mention that my laptop has the same graphic card: ati radeon xpress 200m. 

I tried the vesa driver and it worked, but I didn't stop until I made the ati driver work. I explained how I did this in a previous post. I downloaded the ati driver with apt-get and configured it using fglrxconfig, because dpkg-reconfigure doesn't add some settings which are necessary for this card to work. However, I didn't like this driver either because the screen showed weird things whenever I shut down my computer and this card model isn't specifically supported by this driver.

I downloaded the ati proprietary driver (32 bit version) from 
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)
and configured it using fglrxconfig again. So the version I've got currently working is: 8.21.7
and my /etc/X11/xorg.conf file looks like this:
# File: xorg.conf
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
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

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
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"es"

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
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
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
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
#    BusID "PCI:1:0:0"    # no device found at config time
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


 Hope this helps!!
:mrgreen:

---

### Post by CalvinK on 2006-02-04
I think you may try to reconfigure xserver-xorg choosing the multi purpose driver 'vesa' "sudo dpkg-reconfigure xserver-xorg". Or try to install the fglrx driver from ATI technology (see ATIDRiverHowTo in the wiki). Then, reconfigure the xserver by choosing the fglrx driver. I had the same problem with my laptop Toshiba M40-331.
Good luck !:):D

---

