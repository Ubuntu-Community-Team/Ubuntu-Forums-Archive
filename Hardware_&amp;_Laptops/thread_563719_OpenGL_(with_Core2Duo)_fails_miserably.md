---
title: "OpenGL (with Core2Duo) fails miserably"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by andreeh on 2007-09-30
Greetings.

This is a very common problem nowadays (I've been googling like a frenetic geek last few days trying to figure this out).

Tried this with three different computers, all running Core2Duo's, none of these run okay with OpenGL.

First I thought it was a problem with the OpenGL library from ATI/AMD, but it doesn't seem to be that since the third computer I tried on was running a nvidia card.

Now to the problem;
whenever a OpenGL (or rendering of any kind it seems) the CPU (mainly one core) goes up to weird percentages.

For example, tuxkart runs up one core to 100% and then alternates between them until the computer almost dies of heat.

I've tried Feisty on all three aswell as Gutsy (current), it's still there.

It seems to me that it's some kind of acceleration problem, I've heard (and read) that the mesa-libs run on CPU power, if this is correct, maybe the OpenGL files are cross referenced on compile, so they include the mesa libs also?

I'm all out of ideas here.

xorg.conf
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "se"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "CMC 19AW"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Device0"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Device0"
        Monitor    "CMC 19AW"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1440x900"
        EndSubSection
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

```

/proc/acpi/processor/CPU1/*
```

processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
active state:            C1
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

```

fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6849 Release

```

libGL_debug=verbose glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6849 Release

```

---

### Post by Lord Illidan on 2007-09-30
It is certainly not a problem with the core2duo..I can play Quake 3, Quake 4 and UT 2004 without any problems on this core2duo. I have a nvidia go7400..

---

### Post by andreeh on 2007-09-30
What distro / kernel are you running? Any "special" options in the xorg.conf? Could you please put your "lsmod" in to see if it might be anything - like acpi_* modules - that interfer?

Regards

---

### Post by airbornespent on 2007-10-06
I have the same problem on a thinkpad with a 2Ghz Dothan-755 and ATI FireGL T2 card. The GL screensavers especially rack up the CPU usage. The only reason I noticed this was I just set up the nvidia drivers on a Geforce2 GTS on a P3 1GHz and sadly, 3d acceleration runs much smoother on the GF2 with NO increase in CPU utilization, all the rendering is done by the card. What gives...

From the FireGL thinkpad:

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
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
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
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
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

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc M10 NT [FireGL Mobility T2]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M10 NT [FireGL Mobility T2]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200"
        EndSubSection
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
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

---

