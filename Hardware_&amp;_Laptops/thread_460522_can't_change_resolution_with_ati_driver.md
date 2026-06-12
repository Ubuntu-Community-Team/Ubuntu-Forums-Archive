---
title: "can't change resolution with ati driver"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by fangorious on 2007-05-31
I have an HP Compaq NW8240 with an Ati FireGL V5000 PCI card. Using the ati driver I can't change from the detected native resolution. I filed a bug report [here]("https://bugs.launchpad.net/bugs/111674") but it hasn't been acknowledged in any way. The fglrx driver lets me change resolution, but it doesn't support custom modelines, which I need to use for any non-native widescreen resolutions (1680x1050 and 1440x900)

```

[fangorious@basilisk:~]
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
[fangorious@basilisk:~]
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FireGL V5000
OpenGL version string: 2.0.6334 (8.34.8) 

```

---

### Post by 67GTA on 2007-05-31
You can manually edit your /etc/X11/xorg.conf file and type in the desired resolutions, or boot in to recovery mode and run "sudo dpkg-reconfigure xserver-xorg" and change it that way. If you use the later, it will help to have the monitor resolution modes and refresh rates handy.

---

### Post by fangorious on 2007-05-31
> **67GTA said:**
> You can manually edit your /etc/X11/xorg.conf file and type in the desired resolutions, or boot in to recovery mode and run "sudo dpkg-reconfigure xserver-xorg" and change it that way. If you use the later, it will help to have the monitor resolution modes and refresh rates handy.

I already have all my resolutions in xorg.conf (with custom modelines and refresh rates), it's posted on the launchpad bug I linked to. The ati driver correctly detects all the supported resolutions (even the widescreen ones the fglrx driver doesn't) but when I try to change the resolution the screen goes all crazy (screenshot is attached). I can kill X with ctrl-alt-backspace, but it goes right back to 1920x1200

---

### Post by 67GTA on 2007-05-31
Post your /etc/X11/xorg.conf file.

---

### Post by fangorious on 2007-06-01
```

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
        Load "bitmap"
        Load "ddc"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "vbe"
EndSection

Section "InputDevice"
        Identifier "Generic Keyboard"
        Driver "kbd"
        Option "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc104"
        Option "XkbLayout" "us"
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

Section "Device"
        Identifier "Generic Video Card"
        Driver "ati"
        BusID "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier "Generic Monitor"
        Option "DPMS"
        HorizSync 31.5-91.1
        VertRefresh 60-100
        Modeline "1680x1050@60" 162.00 1680 1704 1792 2136 1050 1201 1204 1249 +hsync +vsync
        Modeline "1440x900@60" 162.00 1440 1464 1552 2136 900 1201 1204 1249 +hsync +vsync
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Generic Video Card"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 1
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 4
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 8
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 15
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen "Default Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
        InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection

```

---

### Post by 67GTA on 2007-06-01
The first resolution in this section is the one it will default to. Try listing the best resolution first.

Section "Screen"
        Identifier "Default Screen"
        Device "Generic Video Card"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 1
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 4
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 8
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 15
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1920x1200" "1680x1050@60" "1440x900@60" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by fangorious on 2007-06-01
I tried setting 1680x1050@60, 1440x900@60, and 1400x1050 as the default, and in all three cases X loaded as it appears in the screenshot from the bug report.

---

