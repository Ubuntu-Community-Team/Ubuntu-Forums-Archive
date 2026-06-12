---
title: "xorg.conf 3dAcceleration"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by S.O.F on 2007-02-09
Hi all, Im after a little help configuring my xorg,conf file, for running dual monitors with 3d acceleration (wanting to put xgl on soon). I've installed the latest ATI drivers for my card, and editted the file to use dual heads, which now work aside from a slight marring of windows when I move them from one screen to another. Im assuming its directly associated with the following error I get when running glxgears or fglrxinfo.

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Am I right in beleiving that seeing Mesa in there means the driver isnt working properly?

My xorg file is as follows

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Screen[Main]" 0 0
        Screen         "Screen[Aux]" LeftOf "Screen[Main]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        Option      "Xinerama" "on"
        Option      "Clone" "on"
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

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
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

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
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
        Identifier   "ILLYAMA-Left"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "ILLYAMA-Right"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Monitor[Main]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:5:0:0"
EndSection

Section "Device"
        Identifier  "Monitor[Aux]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:5:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Screen[Aux]"
        Device     "Monitor[Aux]"
        Monitor    "ILLYAMA-Left"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen[Main]"
        Device     "Monitor[Main]"
        Monitor    "ILLYAMA-Right"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

I've tried reinstalling the drivers, but to no avail. Gonna check if acceleration is working with the original xorg file now. But Id appreciate any help. Im running Kubuntu, on an AMD 64 4000, with ATI x1900xtx. And this is the first time Ive installed linux, though I have used it occassionally.

Cheers in advance.

---

### Post by divague on 2007-02-09
yes, the driver isn't working properly.

I followed this guide and beryl/xgl is running well

[http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

At the end if beryl is installed and you still get metacity try downgrading beryl

---

### Post by S.O.F on 2007-02-09
Thanks for the link, but my problem is more about the dual head than the driver setup (I was deceived by my own title).

I've narrowed the problem down to the line

```


Section "ServerFlags"
   Option "Xinerama" "on"
EndSection

```

When I turn it on (with my current xorg.conf - essentially the same except some driver options added for the card) I get my dual desktop set up exactly how I want, with the K menubar on the right screen, and the left screen empty except for whatever windows I've placed there. Essentially, its identical to the windows dual screen setup.

BUT, with Xinerama on I get the error mentioned earlier. Removing this line, makes my desktop split in two, each monitor behaves as its own desktop, each with K menu, and I cant drag items between the two. BUT, fglrxinfo, gives the right information, and no errors.

I want them set up like happens with xinerama on, but without the errors.

Suggestions?

---

