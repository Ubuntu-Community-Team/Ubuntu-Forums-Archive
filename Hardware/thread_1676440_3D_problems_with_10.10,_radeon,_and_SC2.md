---
title: "3D problems with 10.10, radeon, and SC2"
date: 2011-01-27
forum: Hardware
---

### Post by neogeek23 on 2011-01-27
I'm trying to figure out what my graphics problem in linux is.  I think I don't have proper 3d acceleration or something.  I followed [this]("http://www.ubuntugamer.com/2010/11/starcraft-ii-a-seamless-wine-experience-with-beautiful-graphics/") guide for getting SC2 to work in linux with wine.  [This]("http://www.flickr.com/photos/58838380@N04/5392757618/") is what I end up with.

I have a radeon 3870 and it runs SC2 perfect in ultra on windows, but I'm tried of window's ********.  I would like to be able to make full use of my hardware in linux.  I have the proprietary drivers for my ATI Radeon 3870 card installed (i think).  If I run the game with the basic driver set I get proper a looking interface but no 3D items only blackness.

I read in some other forums about how randr12 has been interfering with the drivers but that was mainly for dual head... which I'm also having some minor troubles with.  My second monitor works but refuses to assume a vertical layout.  I can probably figure that out but I thought I'd mention it encase it could be related.

How do I find out if I properly and completely installed my radeon drivers (Knowing whetether or not I installed things completely in linux is a sense I do not yet have.)?  What does that image seem to say about my graphics?  Most importantly how can I fix this problem?

Thanks in advance for all your help.  Should I be missing any info please let me know.  I will of course be updating this page with any and all needed information.  I think I'll pass out now from a night of beat my head against this wall.  Thanks again.

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "DesktopSetup" "horizontal,reverse"
    Option        "OverlayOnCRTC2" "0"
    BusID       "PCI:1:0:0"
    Option        "EnableRandR12"  "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
    Option        "EnableRandR12"  "false"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes     "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes     "900x1440"
    EndSubSection
EndSection
](*,):-({|=

---

### Post by neogeek23 on 2011-01-27
shameless self bumb

plz help me someone!
:confused:

---

