---
title: "Low Resolution Mode Solved!  Ubuntu 9.10"
date: 2009-12-22
forum: Hardware
---

### Post by ebaker on 2009-12-22
System: Dell Precision 530, dual 1.5GHz, 768M ram, dual 18G SCSI drives, Nvidia Quadro2 Pro card

I was stuck in 800x600 since the install for about 2-weeks ago until I finally figured out that apparently there are no compatible drivers for my card - at least that I could get to work.

I built my own Xorg.conf using the built in nv driver.

I am happy running in 1280x1024 now but is there any way to get out of the software based accelerator for better performance?  Any suggestions for cheap compatible used card that might work with the drivers available?

-------------------------------------------

Section    "Monitor"
    Identifier    "Dell P1130"
    HorizSync    30.0 - 130.0
    VertRefresh    48.0 - 170.0
    DisplaySize    404 302
EndSection

Section "Device"
    Identifier "Default Device"
    Driver    "nv"
    Option    "DCC"    "1"
    Option    "NoAccell"    "0"
EndSection

Section    "Screen"
    Identifier    "Default Screen"
    Monitor    "Dell P1130"
    Device    "Default Device"
    DefaultDepth    24
    SubSection    "Display"
        Depth    24
        Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section    "ServerLayout"
    Identifier    "Default Layout"
    Screen    "Default Screen"
EndSection

---

