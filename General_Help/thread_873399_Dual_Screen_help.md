---
title: "Dual Screen help"
date: 2008-07-29
forum: General Help
---

### Post by rhenium3 on 2008-07-29
Hello, I need help! I tried to set up my dual screen mode in ubuntu.  I have a MSI PR200, and I used the instructions found here:

[https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200](https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200)

which says to add this:

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "Off"
EndSection

Section "Monitor"
        Identifier      "Philips 170S"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Philips 170S"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
                Virtual 2624 2048
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection

to /etc/X11/xorg.config   I did so and the resolution of the screen is way to big and I can't access the menu bar, only a few icons my desktop. I backed up the original file, and when I put it back the screen resolution is still too big.  I tried right clicking on the desktop to change it, but alas, I am no longer in windows.  

Is there an easy way to do this without going into bios?  I have access to the terminal.  Please let me know! Thanks

---

### Post by rhenium3 on 2008-07-29
bump plus more info..

Maybe the launch bar is just missing? It seems when I maximize windows they only go to the edge of the screen so...  Any help would be appreciated, thanks!

---

### Post by rhenium3 on 2008-07-29
Turns out my gnome-panel was missing, so I reinstalled it... got some bugs, just deleted them and now it *seems* to work fine :)

---

