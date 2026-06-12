---
title: "Strange UI and graphic problems with Jaunty + ATI R100 + 19' Benq LCD"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by jorgeblasio on 2009-08-20
Hey guys, I've been fiddling around with Jaunty for about a month and I came across a couple of issues and I can't seem to find a solution or an explanation. It's kinda hard to describe it, so cope with me.

I've an old  computer I built from scrap parts from 2 computers. It's an Athlon @ 1.2 Ghz on a Socket A MoBo from PC Chips. I've got 512 RAM, not DDR,plain DIMMS, 2 H.D.D.'s (one 60Gb and the other 40 Gb). The graphics card is an ATi RV100 Radeon 7000/VE with 128 Mb RAM hooked up to a brand new Benq 18.5' LCD monitor model g920HD with a native res of 1366x768@65 Hz. I have it running ok with compiz enabled and I've configured my xorg with all the options to improve the video (btw, I'm using the radeon drivers) and I'm getting this strange issue: 

All of the UI goes wobbly and jumpy when the system produces a video refresh!

If I move a window I get artifacts and everything onscreen shakes until I leave the window alone. If I activate a contextual menu, everything shakes again until the menu is displayed. There is of course a lot of tearing. Flash videos don't drop too many frames and are completely watchable inside their windows (which oddly enough don't produce any issues while playing back). I'm also missing around 20 pixels from the right edge of my screen, there is a black bar. Here's what puzzles me the most: I've WindowsXP on a secondary partition and when I booted up for the first time, the video would behave exactly the same with the generic ATi drivers XP comes with. That is, until I installed the ATi Catalyst drivers, after restarting into Windows, voila! No more artifacts, jumpiness and the screen would render all of the 1366x768 pixels, no black bar on the right. It's really frustrating.

Here's my xorg.conf file:

```

Section "Monitor"
    Identifier    "Benq G920HD"
    VendorName    "BNQ"
    ModelName    "G920HD"
    Option        "DPMS"
    HorizSync       30-63
    VertRefresh     50-76
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Benq G920HD"
    Device        "Radeon 7000"
    SubSection "Display"
        Modes           "1366x768" "1280x720"
    EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "Device"
    Identifier    "Radeon 7000"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option        "UseFBDev"        "true"
    Option        "TripleBuffer"        "True"
    Option "AccelMethod" "EXA"
    Option "MigrationHeuristic" "greedy"
    Option "AGPMode"    "4"
EndSection

Section "ServerLayout"
    Identifier      "Default Layout"
    Screen          "Default Screen"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection

```Any help is REALLY appreciated :D
BTW, at 1024x768 the problems go away but since it's not the native res, everything is blurry.

---

