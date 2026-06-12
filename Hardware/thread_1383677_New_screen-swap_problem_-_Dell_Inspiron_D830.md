---
title: "New screen-swap problem - Dell Inspiron D830"
date: 2010-01-17
forum: Hardware
---

### Post by Malibyte on 2010-01-17
Hi all -

I have a Dell Inspiron D830 laptop, running Karmic, with a D/Dock, which two external displays - a ViewSonic Q241wb LCD monitor and a Samsung HDTV (1080p)...I sometimes use the docked laptop as a MythTV frontend in an upstairs room. 

Prior to about a month ago, I could use "Scroll Lock+F8" (with the external keyboard) or "Fn+F8" on the laptop's keyboard to alternate between displays - (laptop screen, LCD monitor, or TV individually; I could also run any two of them at once).

This no longer works.  Now, the laptop screen and the LCD always come up (both).  Neither key combination changes the display as it had before.

I suspect that this is either an Xorg bug or a problem with the nVidia kernel driver (using a dkms modular install; now using version 190.53 with 2.6.31-17 generic kernel).  I have both Gnome and KDE desktops on the machine (WindowMaker also), doesn't matter which I boot to, still doesn't work.

The key combination DOES work at the GRUB screen, so it's not a BIOS problem.

Just wondering whether anyone else has seen this problem.  

I have a rather involved xorg.conf file which had worked fine (did everything I wanted) up until a month or so ago.  The "generic" skeleton xorg.conf file doesn't allow me to use anything other than the laptop screen, even docked; at least with mine I get the laptop screen + the LCD.  

Tried using "sudo nvidia-settings" but the changes it makes to the xorg.conf file don't solve the problem. 

```

Section "Monitor"
        Identifier      "ViewSonic LCD"
        HorizSync       30-80
        VertRefresh     50-61
        Option          "DPMS"
        Option          "TwinView"      "True"
        Modeline        "1920x1200" 150.75 1920 2016 2048 2185  1200 1202 1208 1235
        Modeline        "1680x1050" 119.12  1680 1728 1760 1840  1050 1052 1058 1080
        Modeline        "1440x900"  119.12  1440 1728 1760 1840  900 1052 1058 1080
EndSection

Section "Monitor"
        Identifier      "Dell 1920x1200 LCD"
        HorizSync       30-81
        VertRefresh     56-75
        Option          "DPMS"
        Option          "TwinView"      "True"
        Modeline        "1920x1200" 150.75 1920 2016 2048 2185  1200 1202 1208 1235
        Modeline        "1680x1050" 119.12  1680 1728 1760 1840  1050 1052 1058 1080
        Modeline        "1440x900"  119.12  1440 1728 1760 1840  900 1052 1058 1080
EndSection

Section "Monitor"
        Identifier      "Samsung HDTV"
        VendorName      "Samsung"
        ModelName       "HLT-5687S"
        HorizSync       30.0-90.0
        VertRefresh     50.0-75.0
        Option          "TwinView"      "True"
        Option          "DPMS"
        ModeLine        "1808x1016_60" 152.5 1808 1920 2112 2416 1016 1017 1020 1052 -hsync +vsync
        ModeLine        "1920x1080_60" 172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
        ModeLine        "1600x900_60"  119.00  1600 1696 1864 2128  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "D830nVidia"
        Monitor         "ViewSonic LCD"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes   "1920x1200" "1680x1050" "1440x900" "1600x1200" "1280x1024"
        EndSubSection
EndSection

Section "Module"
        Load "dbe" # Double-Buffering Extension
        Load "v4l" # Video for Linux
        Load "extmod"
        Load "freetype"
        Load "glx" # 3D layer
        Load "fbdevhw"
        Load "record"
        Load "type1"
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Device"
        Identifier      "D830nVidia"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
#       Option          "AddARGBVisuals"        "True"
#       Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "False"
#       Option          "UseEvents"     "True"
        Option          "TwinView"      "True"
        Option          "TwinViewOrientation" "Clone"
        Option          "MetaModes" "1920x1200, 1920x1200, 1920x1080_60 @1920x1200"
        Option          "HorizSync"   "CRT-0: 30-80;  DFP-0: 30-80; DFP-1: 30-90"
        Option          "VertRefresh" "CRT-0: 50-61;  DFP-0: 50-61; DFP-1: 50-75"
        Option          "ConnectedMonitor" "CRT-0, DFP-0, DFP-1"
EndSection


```

---

### Post by shakma on 2010-01-25
No real advice here, just a bump w/ my own experience.  I am running 9.10 on a Dell Inspiron 1100. (<-- Mmm, hmm!  That's right!)  After editing the Sync and Refresh rates in xorg.conf, I am able to get proper resolution and rarely have video "blackouts".  

However, I have also found that Fn+F8 (CRT/LCD swap) does nothing.  After reading this post and playing around some, I found that it works at the GRUB menu, and if hooked up to the projector *BEFORE* turning on the laptop, from Usplash on, ONLY the projector display functions.  Fn+F8 will not bring it back to the laptop screen, _even if I unplug the projector cable._ I have to reboot *without* the projector cable attached to get the display back on the laptop screen.

So, any advice?

Bump.

P.S.  I may try your xorg.conf with some editing.  A cloned dual-screen would be a little better for my purposes (basic computer instruction classes).

---

