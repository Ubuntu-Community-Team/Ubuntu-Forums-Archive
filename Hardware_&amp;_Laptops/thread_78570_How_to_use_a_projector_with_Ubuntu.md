---
title: "How to use a projector with Ubuntu"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by sindrejh on 2005-10-18
I'm not sure this is the right forum, but:

I have a Dell Latidude c800 laptop, and wants to use a prjector with it. The problem is that noting happens when I try to press [Fn]+[F8](CRT/LCD).

My first tought was that the fn-button was the problem. Because the same thing happen (or do not happen) on windows. But i can use the fn combinations to turn the sound up/down.

If nobody has a good solution, my question is:
Can I install a program witch I can use to get an output to my projector, or a command or something else?

Thanks

---

### Post by bluck on 2005-10-18
[QUOTE=sindrejh]I'm not sure this is the right forum, but:

I have a Dell Latidude c800 laptop, and wants to use a prjector with it. The problem is that noting happens when I try to press [Fn]+[F8](CRT/LCD).

My first tought was that the fn-button was the problem. Because the same thing happen (or do not happen) on windows. But i can use the fn combinations to turn the sound up/down.

If nobody has a good solution, my question is:
Can I install a program witch I can use to get an output to my projector, or a command or something else?

Thanks[/QUOTE]

I'm thinking you would have to edit your xorg.conf to accomodate the second display.

here's mine for dual display on my desktop, im sure you'll have to make some changes tho:
```

Section "ServerLayout"
        Identifier     "Multihead layout"
        Screen      0  "Screen0" leftof "Screen1"
        Screen      1  "Screen1" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        Option      "Xinerama" "on"
        Option      "Clone" "off"
        InputDevice     "eraser" "AlwaysCore"
        InputDevice     "stylus" "AlwaysCore"
        InputDevice     "cursor" "AlwaysCore"
        InputDevice     "pad" "AlwaysCore"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name
 
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

# Multiple FontPath entries are allowed (they are concatenated together)
# By default, Red Hat 6.0 and later now use a font server independent of
# the X server to render fonts.

        RgbPath      "/usr/X11R6/lib/X11/rgb"
        FontPath     "unix/:7100"
EndSection

Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "fbdevhw"
        Load  "glx"
        Load  "record"
        Load  "freetype"
        Load  "type1"
        Load  "dri"
EndSection

Section "InputDevice"
# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#       Option  "Xleds"         "1 2 3"

# To disable the XKEYBOARD extension, uncomment XkbDisable.
#       Option  "XkbDisable"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#       Option  "XkbModel"      "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#       Option  "XkbModel"      "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#       Option  "XkbLayout"     "de"
# or:
#       Option  "XkbLayout"     "de"
#       Option  "XkbVariant"    "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#       Option  "XkbOptions"    "ctrl:swapcaps"
# Or if you just want both to be control, use:
#       Option  "XkbOptions"    "ctrl:nocaps"
#
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "yes"
EndSection

Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option      "Type" "stylus"
    Option      "Mode" "relative"
    Option        "Device"        "/dev/input/event2"
    Option        "USB"           "on"
EndSection

Section "InputDevice"
    Identifier  "eraser"
    Driver      "wacom"
    Option      "Type" "eraser"
    Option      "Mode" "relative"
    Option        "Device"        "/dev/input/event2"
    Option        "USB"           "on"

EndSection

Section "InputDevice"
    Identifier  "pad"
    Driver      "wacom"
    Option      "Type" "pad"
    Option      "Mode" "relative"
    Option        "Device"        "/dev/input/event2"
    Option        "USB"           "on"

EndSection

Section "InputDevice"
    Identifier  "cursor"
    Driver      "wacom"
    Option      "Type" "cursor"
    Option      "Mode" "relative"
    Option        "Device"        "/dev/input/event2"
    Option        "USB"           "on"

EndSection


Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "NEC FE2111SB"
        DisplaySize  400        300
        HorizSync    30.0 - 115.0
        VertRefresh  50.0 - 160.0
        Option      "dpms"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "NEC MultiSync FP912SB"
        HorizSync    30.0 - 110.0
        VertRefresh  50.0 - 160.0
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "ati"
        VendorName  "Videocard vendor"
        BoardName   "ati"
EndSection

Section "Device"
        Identifier  "Videocard1"
        Driver      "ati"
        VendorName  "Videocard Vendor"
        BoardName   "ati"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x1024" 
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Videocard1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x1024"
        EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection

```

good luck :)

---

### Post by sindrejh on 2005-10-18
Thanks! i opened the xorg.conf file, tried  a  "sudo dpkg-reconfigure -phigh xserver-xorg" as the file said, when the projector was connected. And the everything just worked. :) 

Sindre

---

### Post by bluck on 2005-10-18
[QUOTE=sindrejh]Thanks! i opened the xorg.conf file, tried  a  "sudo dpkg-reconfigure -phigh xserver-xorg" as the file said, when the projector was connected. And the everything just worked. :) 

Sindre[/QUOTE]

nice work ;)

---

