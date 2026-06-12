---
title: "Monitor Samsung Syncmaster 223BW and obtain a right 1600x1050 resolution..."
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Garret88 on 2007-08-01
I have an integrated intel video card(the model is 82865G), so i have to use i810 driver...

Yesterday i have bought this monitor
(info are *[here]("http://www.pixmania-pro.co.uk/uk/uk/516268/art/samsung/syncmaster-223bw-21-6-wid.html")*, i didn't find the product on samsung site :(). The monitor so works correctly with a 1600x1050 resolution.

Now i have a problem. When i go to gnome reolution tool i see the 16**8**0x1050 res(but not the right 16**0**0x1050) and if i select this i obtain an about 1400xSOMEWHAT resolution. While in the Xorg.conf all resolutions are set right.

I have also tried this [guide]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e") (about the i810 drivers and the 915 resolution), but nothing :(.

Here there is my _**xorg.conf**_:

```
[SIZE=1]Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "it"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection[/SIZE]

[COLOR=Red]Section "Device"
    Identifier    "Intel Corporation 82865G Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster 223BW"
    Option        "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82865G Integrated Graphics Controller"
    Monitor        "Samsung SyncMaster 223BW"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1600x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection[/COLOR]
[SIZE=1]
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection[/SIZE]
```

---

