---
title: "D620 Nvidia"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by rdunnam on 2006-10-20
Hello all.
I am new to Ubuntu and not a *nix expert by any means.  I have used FC mostly in the past, started in RH9 days.  I have never had to deal with xorg stuff and am getting my tail kicked trying to get this set up working.
I am trying to get it to where I can have my laptop open and have my external monitor connected via docking station, which is actually a projector connected to the port replicator,to have thedisplay cloned.  However, I have been able to get it to show up in just the laptop screen or just the projector, but never both.  At this point getting it to just have both on and 'span' the desktop would be fine.  Although I dont like to let things go.  So I will attach my xorg.  I am running the 'nvidia' driver.  Note, if I put it on a dock with a monitor, flat panel, it will clone but not fit the resolution to the flat panel's needed resolution.  Any help will be appreciated.  I have tried tons of options but with no success.  But as stated I am not a master of X.

Thanks for all the help.

---

### Post by azvoleff on 2006-10-31
I use my D620 with an external LCD (but without a docking station).  I set up two separate x-screens to easily allow the use of separate resolutions on each monitor.  Note this is not TwinView, where you can drag windows across your desktop.  Just set up another device section identical to what you already have, but eliminate the metamodes and twinview lines, and change the identifier for the second entry.  You will also need to change your serverlayout section, and make one monitor use the second nVidia output.  See the relevant sections of my xorg (below) for an example.

Section "ServerLayout"
    Identifier	"Default Layout"
    Screen	0 "Laptop Screen" 0 0
    Screen	1 "Other Screen" Below "Laptop Screen"
    InputDevice	"Generic Keyboard"
    InputDevice	"Configured Mouse"
    InputDevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
    Identifier     "Laptop Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Samsung Syncmaster 205BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "NVIDIA Out 0"
    Driver         "nvidia"
    Screen 0
    Option	   "NoLogo" "true"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "NVIDIA Out 1"
    Driver         "nvidia"
    Screen 1
    Option         "NoLogo" "true"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Laptop Screen"
    Device         "NVIDIA Out 0"
    Monitor        "Laptop Monitor"
    DefaultDepth   24 
    SubSection     "Display"
        Depth       16
        Modes      "1440x900 800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900 800x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Other Screen"
    Device         "NVIDIA Out 1"
    #Monitor        "Samsung Syncmaster 204T"
    Monitor        "Samsung Syncmaster 205BW"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050 1600x1200 1280x1024 800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050 1600x1200 1280x1024 800x600"
    EndSubSection
EndSection

---

