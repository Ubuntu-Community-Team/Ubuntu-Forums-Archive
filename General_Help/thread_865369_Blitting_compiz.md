---
title: "Blitting compiz"
date: 2008-07-20
forum: General Help
---

### Post by callmeishmael on 2008-07-20
Having a problem with 3d effects (Compiz) on my macbook.

It is a first gen. Macbook with Intel 945 GMA card. The xorg.conf looks like (the relevent bits)

[code]
Section "ServerLayout"
    Identifier      "MacBook - First Generation"
    InputDevice     "Mouse1" "CorePointer"
    InputDevice     "Keyboard1" "CoreKeyboard"
    InputDevice     "Synaptics Touchpad"
    Screen          "Screen 1"
# Beryl/Compiz - AIGLX built in xorg-server 7.1 and >
#    Option          "AIGLX" "true"
EndSection

Section "Extensions"
# Beryl/Compiz
     Option         "Composite"               "Enable"
EndSection

Section "Module"
    Load            "glx"
    Load            "extmod"
    Load            "xtrap"
    Load            "record"
    Load            "dbe"
    Load            "dri"
    Load            "freetype"
    Load            "type1"
    Load            "synaptics"
# Disabled for AIGLX
#    Load            "GLcore"
#    Load            "vbe"
EndSection

Section "Device"
    Identifier      "i945GM"
    Driver          "intel"
    VendorName      "Intel Corporation"
    BoardName       "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
# Beryl/Compiz
    Option          "DRI"     "true"
    Option          "XAANoOffscreenPixmaps" "true"
# Xorg.0.log was spitting warnings about BusID
#    BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier      "Built-in LCD"
    VendorName      "APP"
    ModelName       "9c5f"
# Hope the values are correct.  Taken from Debian Wiki.  Saw no values in documentation.
    HorizSync       28-64
    VertRefresh     43-60
EndSection

Section "Screen"
    Identifier      "Screen 1"
    Device          "i945GM"
    Monitor         "Built-in LCD"
    DefaultDepth    24
    SubSection "Display"
        Viewport    0 0
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection
[\code]

and the output

[code]
<hostname>$ glxinfo| grep 'direct'
direct rendering: Yes
[\code]

However, when I load compiz and emerald (via fusion-icon or otherwise)
I encounter a huge number of 'artefacts' (black pixels) that hover around the windows and make it nigh on impossible to use (and so it's left off for now) and is horrendously slow. Has anyone else encountered/fixed this?

I've searched the forums but all I seem to get are howto's on setting up AIGLX.

---

### Post by poofyhairguy on 2008-07-20
> **callmeishmael said:**
> Having a problem with 3d effects (Compiz) on my macbook.

It is a first gen. Macbook with Intel 945 GMA card. The xorg.conf looks like (the relevent bits)

[code]
Section "ServerLayout"
    Identifier      "MacBook - First Generation"
    InputDevice     "Mouse1" "CorePointer"
    InputDevice     "Keyboard1" "CoreKeyboard"
    InputDevice     "Synaptics Touchpad"
    Screen          "Screen 1"
# Beryl/Compiz - AIGLX built in xorg-server 7.1 and >
#    Option          "AIGLX" "true"
EndSection

Section "Extensions"
# Beryl/Compiz
     Option         "Composite"               "Enable"
EndSection

Section "Module"
    Load            "glx"
    Load            "extmod"
    Load            "xtrap"
    Load            "record"
    Load            "dbe"
    Load            "dri"
    Load            "freetype"
    Load            "type1"
    Load            "synaptics"
# Disabled for AIGLX
#    Load            "GLcore"
#    Load            "vbe"
EndSection

Section "Device"
    Identifier      "i945GM"
    Driver          "intel"
    VendorName      "Intel Corporation"
    BoardName       "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
# Beryl/Compiz
    Option          "DRI"     "true"
    Option          "XAANoOffscreenPixmaps" "true"
# Xorg.0.log was spitting warnings about BusID
#    BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier      "Built-in LCD"
    VendorName      "APP"
    ModelName       "9c5f"
# Hope the values are correct.  Taken from Debian Wiki.  Saw no values in documentation.
    HorizSync       28-64
    VertRefresh     43-60
EndSection

Section "Screen"
    Identifier      "Screen 1"
    Device          "i945GM"
    Monitor         "Built-in LCD"
    DefaultDepth    24
    SubSection "Display"
        Viewport    0 0
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection
[\code]

and the output

[code]
<hostname>$ glxinfo| grep 'direct'
direct rendering: Yes
[\code]

However, when I load compiz and emerald (via fusion-icon or otherwise)
I encounter a huge number of 'artefacts' (black pixels) that hover around the windows and make it nigh on impossible to use (and so it's left off for now) and is horrendously slow. Has anyone else encountered/fixed this?

I've searched the forums but all I seem to get are howto's on setting up AIGLX.

You can't # out the PCI:ID like that.

Hmmmmmm. My Macbook always did well for me out of the box in 7.10 (I have given it to my sister since then so I cannot go see what my Xorg was.

Honestly as a Xorg hacker myself, it seems you have the problem of modifying your Xorg too much. It is a very sensitive file. My best advice is try downloading the newest Ubuntu or Fedora live cd and email yourself the Xorg.conf file it makes.

---

