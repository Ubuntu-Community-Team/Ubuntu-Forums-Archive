---
title: "Radeon driver 16-bit color mode gives blueish background in X-Windows"
date: 2011-11-29
forum: Hardware
---

### Post by jthompson7804 on 2011-11-29
Hi all.  I'm new to UBUNTU as I've just installed it last weekend but I'm having trouble using my ATI Radeon HD3870 based graphics card in 16-bit color mode.  The fglrx drivers don't support 16-bit color so I'm using the "radeon" open source driver.  

Everything works fine in 24-bit color mode but if I add the line "DefaultDepth 16" to the xorg.conf file, then the window system develops a blue background.  If I run xgamma from the terminal window to change the gamma values, adjustments to red or green make a change (but rgamma or ggamma above 2.0 make the image too bright), but changing -bgamma has no effect whatsoever on the image (whether I set -bgamma to 0.1 or 9.0, for instance).  

Is this a normal problem to have?  Is there any ideas on how I can resolve it?

Here is an excerpt of my xorg.conf file:

"    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon HD 3870"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
    DefaultDepth    16
EndSection"

---

