---
title: "ATI X300 and MergedFB"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by jkugler on 2008-02-25
I've googled, searched this board, read lots of pages (including [http://ubuntuforums.org/showthread.php?t=301961]("http://ubuntuforums.org/showthread.php?t=301961") and tried many things, but I simply CANNOT get MergedFB to work with my Radeon X300 card.

Specs:
Dell Latitude D610
Radeon X300 with 64MB RAM
External Viewsonic VX2035wm (1680x1050 native), on analog VGA
1024x768 native on the laptop.
Ubuntu Gutsy

I've tried using Xinerama, but with ati, radeon, and fglrx drivers it results in screen corruption and/or hard lockups.  So, I am trying for MergedFB.

I'll post my config at the end, but what I am getting is this.  The laptop display is displaying fine at 1024x768.  But the external display is mirroring *and* displaying at 800x600.  I can't for the life of me figure out what to do to get the external to display correctly.

Any ideas?

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "microsoft"
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
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MonitorLayout"         "LVDS, TMDS"
        Option          "MergedFB"              "true"
#       Option          "CRT2HSync"             "30-81"
#       Option          "CRT2VRefresh"          "56-75"
        Option          "CRT2Position"          "LeftOf"
        Option          "MetaModes"             "1024x768-1680x1050"
        Option          "MergedNonRectangular"  "true"
        Option          "MergedMouseRestriction"        "true"
        Option          "MergedDPI" "100 100"

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "2704x1050 1024x768"
                Viewport 0 0
                Depth 24
        EndSubSection
        SubSection "Display"
                Virtual         2704 1050
                Viewport 0 0
                Depth 24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        #Screen         "Default Screen"
        Screen      0  "DefaultScreen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Module"
    Load  "IA"
    Load  "dbe"
    Load  "extmod"
    Load  "record"
    Load  "xtrap"
    Load  "GLcore"
    Load  "glx"
    Load  "dri"
    Load  "xtsol"
    Load  "bitstream"
    Load  "freetype"
    Load  "type1"
EndSection

Section "ServerFlags"
        #Option          "Xinerama"      "true"
        Option                 "xrandr"        "true"
EndSection

```

---

### Post by Yellow Pasque on 2008-02-26
Merge the two Display sections, i.e:
```
SubSection "Display"
        Modes        "1024x768"
        Viewport     0 0
        Depth        24
        Virtual      2704 1050
EndSubSection
```

---

### Post by jkugler on 2008-02-26
> **Temüjin said:**
> Merge the two Display sections, i.e:
```
SubSection "Display"
        Modes        "1024x768"
        Viewport     0 0
        Depth        24
        Virtual      2704 1050
EndSubSection
```

Thanks for the tip, but no joy.  The display looks the same.

```

        SubSection "Display"
                Modes           "2704x1050 1024x768"
                Viewport 0 0
                Depth 24
                Virtual         2704 1050
        EndSubSection

```

And I also tried making the Modes line just:

Modes          "1024x768"

But that didn't do anything different.

Thanks!

j

---

### Post by Yellow Pasque on 2008-02-26
Hi, you tried the Display section exactly as I gave it to you, right? If you used this:
```
Modes           "2704x1050 1024x768"
```
it will confuse X because you have two modes in one quote. Also, 2704x1050 isn't a valid mode.

---

### Post by jkugler on 2008-02-27
> **Temüjin said:**
> Hi, you tried the Display section exactly as I gave it to you, right? If you used this:
```
Modes           "2704x1050 1024x768"
```
it will confuse X because you have two modes in one quote. Also, 2704x1050 isn't a valid mode.

I tried it both, ways, I think.  But I just tried this:

```
SubSection "Display"
        Modes        "1024x768"
        Viewport     0 0
        Depth        24
        Virtual      2704 1050
EndSubSection

```

And it was still doing the same thing of a "mirrored" 800x600 version on the large external monitor.

Thanks again!

j

---

