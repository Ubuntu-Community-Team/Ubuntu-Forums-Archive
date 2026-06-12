---
title: "Keyboard mappings Macbook Pro"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Technoviking on 2006-10-27
I'm having trouble mapping my left and right mouse buttons to the right and left Apple keys on my Macbook Pro.

Here is my .xmodmap
```
keycode 115 = Alt_L Meta_L
add mod1 = Alt_L Meta_L

keycode 101 = F1
keycode 212 = F2
keycode 160 = F3
keycode 174 = F4
keycode 176 = F5
keycode 214 = F7
keycode 215 = F8
keycode 216 = F9
keycode 217 = F10

keycode 116 = Pointer_Button2
keycode 108 = Pointer_Button3
```

And here is my xorg.conf
```


Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "ctrl:nocaps"
        #Option          "XkbOptions"    "ctrl:swapcaps"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "TapButton1"            "0"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "backingstore"  "true"
        Option          "RenderAccel"   "true"
        Option          "DesktopSetup"  "0x00000100"  # clone
        Option          "MonitorLayout" "LVDS,CRT"
        Option          "MetaModes" "1600x1200-1024x768 1600x1200-1280x1024 1600
x1200-1600x1200"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-111
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

Thanks

---

### Post by rdwtux on 2006-10-27
I have a Macbook, not a Pro, but from what I see your xmodmap says that your "small enter" key, the one on the right-hand side of the keyboard is your right-click button.   That's the method most Macbook users are going with as it appears the synaptic drivers (released versions) don't support the appletouchpad. 

There's a Gentoo wiki on getting the touchpad to work but it's ugly.. otherwise the only way to use a right-click on the macbook that I know of is to use the small enter-key on the right side of the touchpad. 

Here's the link to the Gentoo page.  I haven't tried it yet.. it's ugly.

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11)

---

### Post by Technoviking on 2006-10-27
Neither the Apple keys or the small enter key is working.

---

### Post by idn on 2006-10-27
I have a script running under /usr/bin/enable-button3 which contains

#!/bin/bash
xmodmap -e 'keycode 108 = Pointer_Button3'
xkbset m

then in my gnome session apps I just add the program 'enable-button3'

Works well for me, sure you can mod it to get your middle mouse button working

---

