---
title: "Blitty compiz"
date: 2008-08-01
forum: General Help
---

### Post by hack_benjamin on 2008-08-01
Using ubuntu 8.04 on macbook gen 1 (intel 945GM gpu) and have tried both intel and i810 graphics drivers in my xorg.conf which reads:

```

Section "ServerLayout"
    Identifier      "MacBook - First Generation"
    InputDevice     "Mouse1" "CorePointer"
    InputDevice     "Keyboard1" "CoreKeyboard"
    InputDevice     "Synaptics Touchpad"
    Screen          "Screen 1"
EndSection

Section "Extensions"
     Option         "Composite"               "Enable"
EndSection

Section "Files"
    RgbPath         "/usr/share/X11/rgb"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/misc/"
    FontPath        "/usr/share/fonts/Type1/"
    FontPath        "/usr/share/fonts/TTF/"
    FontPath        "/usr/share/fonts/OTF"
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
EndSection

Section "InputDevice"
... CLIP ...
EndSection

Section "InputDevice"
... CLIP ...
EndSection

Section "Device"
    Identifier      "i945GM"
    Driver          "i810"
    VendorName      "Intel Corporation"
    BoardName       "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
    Option          "DRI"     "true"
    Option          "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
    Identifier      "Built-in LCD"
    VendorName      "APP"
    ModelName       "9c5f"
    HorizSync       28-64
    VertRefresh     43-60
    Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
    Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
    Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
    Modeline "640x480_60.00"  23.86  640 656 720 800  480 481 484 497  -HSync +Vsync
EndSection

Section "Screen"
... CLIP ...
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection

```

Anyone any ideas? With metacity it looks fine. It was working until about a week ago when upgrades happened... but I cannot remember what was updated... :(

---

### Post by rainwalker on 2008-08-03
Unfortunately I have no suggestions for you...but would you mind sharing that wallpaper? I'm sorry, but I really like it :)

---

