---
title: "Cannot Exit X11 Session w/ ATI Binary"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by jeelliso on 2007-02-20
Hello,

I've followed the HOWTO [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a") on installing the binary ATI driver by downloading the latest driver from ATI.  I can login successfully and the results of fglrxinfo shows that the ATI driver is functioning.  But here's the problem:  any time I try to exit the X11 session that uses the binary ATI driver the computer goes into a hard freeze (screen is solid black...no keyboard response...fan runs at high speed); I've tried just logging out and using Ctrl-Alt-Backspace and I get the same results; if I change the xorg.conf back to the vesa driver, everything works fine.

Does anybody know what could be going on or how I could try to fix it.  Otherwise, I'll just have to use the vesa driver.

By the way, I'm using Xubuntu 6.10 with very little installed other than the default installation.

Thanks,
~Justin

---

### Post by Richard Kut on 2007-02-27
Hello jeelliso! I don't know a ton about this video stuff, but I will try to help you as best I can.

First off, you need to update this post with the make and model of your graphics card.

Second, please post the contents of your /etc/X11/xorg.conf file.

That should provide enough context for some of the other people in these forums to be able to add their comments.

There is a script which will automatically download and setup the latest ATI (or nVidia) drivers. You can get the script here:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I only suggest this in case the existing setup is flawed in some subtle way. Rather than chasing after shadows, it may be more expedient to just reinstall the driver using a tried and tested (and automated) method.

Please update this post with your feedback, and good luck!

---

### Post by jeelliso on 2007-02-27
Thanks for the reply; I was not aware such a program existed; thanks.  So here's what I did: 1.) I uninstalled the ATI driver that I set up myself; 2.) I installed envy and let it set up the ATI driver.  After reboot, fglrxinfo confirmed that the ATI driver was in use.  Unfortunately, I was still not able to exit the X11 session without doing a hard reset.

Here is the relevant line of lspci:
```
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
```

And here is the xorg.conf file after envy modified it (with comment lines removed):
```
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
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "dbe"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "ati"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```
Any other suggestions are appreciated.  Thanks, Justin

---

### Post by Richard Kut on 2007-02-27
Hello Justin! Sorry that it didn't work. I don't have the same card as you - it's an ATI mobility 9000 IGP, which xorg reports as a Radeon Mobility 9100 U3 (R200 IGP).

One thing that I do know is that my model does not support 3D acceleration like that required for most games.

I will post my xorg.conf file for you to look at, just in case you might find it useful. Here it is:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
        FontPath        "/usr/share/fonts/X11/misc"
#       FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
#       Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IG
P)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IG
P)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection


---

### Post by jeelliso on 2007-03-02
Thanks for the reply.  When I use the open source ati driver, like the one you're using, I don't have any problems.  Its the fglrx binary drive that gets me.  I did a little more research on the subject; I set up an ssh daemon and logged in remotely.  I then recreated the error to see if the entire system was frozen or not.  As it turns out, the Xorg process is just locking up the keyboard, mouse, and monitor and the computer is still running; I was able to move around like normal.  Here is the contents of ~/.xsession-errors prior to logging back out graphically:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jellison"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (xfwm4:5005): WARNING **: The display does not support the XComposite extension.

** (xfwm4:5005): WARNING **: Compositing manager disabled.
```

and here is the additional content after trying to logout:
```
xscreensaver: 11:25:18: 0: unrecognised ClientMessage "_NET_WM_STATE" received
xscreensaver: 11:25:18: 0: for window 0x8000d4 (xfce4-session / Xfce4-session)
xscreensaver: 11:25:19: -1: unrecognised ClientMessage "_NET_WM_STATE" received
xscreensaver: 11:25:19: -1: for window 0x8000d4 ((null) / (null))

(xfce4-battery-plugin:5020): libxfce4util-CRITICAL **: xfce_rc_write_entry: assertion `value != NULL' failed

(xfce4-battery-plugin:5020): libxfce4util-CRITICAL **: xfce_rc_write_entry: assertion `value != NULL' failed
xscreensaver: 11:25:19: -1: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 11:25:19: -1: for window 0x1400057 ((null) / (null))

```

Now if I try to kill the Xorg process by issuing a 'kill -9' the entire system freezes;  I can no longer function via ssh.

I hope this helps somebody.

~Justin

---

### Post by jeelliso on 2007-03-02
I found a work around that seems to do the trick.  Apparently the AMD Quiet & Cool technology is powered, by default, by the powernow-k8 module.  It is also apparent that the ATI binary module and the powernow-k8 module do not play nice together.  So I removed the powernow-k8 module and blacklisted it.  This seems to have done the trick.  It may kill my battery life, but I don't ever use it without the power supply anyways.

---

