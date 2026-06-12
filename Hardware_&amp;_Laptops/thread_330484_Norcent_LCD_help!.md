---
title: "Norcent LCD help!"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by Spoone on 2007-01-03
Hi all..first post, so go easy on me:cool: 

I have a Norcent LCD monitor, model# LM-965WA.  The native resolution is 1440x900.

My problem is that when I boot into Ubuntu (6.10) it won't give my "default" settings, which are the monitor's native ones.

I've tried using the "XorgGUI" tool, to no avail, tried editing the xorg configuration file (which hosed the config in every case..not too confident of doing that again...)

In fact, when I try to set the resolution via the system/preferences dropdown, there's no option for 1440x900 on the list.  None.  I am not amused.  The only way to get the rez I want is to use the Nvidia panel (Alberto Milone's "bleeding edge" listing...)...and even then, that won't stick from one boot to the next.

Anybody able to offer some help?


(And currently, I've nuked my ubuntu install for Vista right now, so I can get at least some decent support for the monitor...but I want my Ubuntu back!)

Thanks much in advance...

Spoone

---

### Post by Spoone on 2007-01-05
I'm back to 6.06.
I still can't get 1440x900 as my default rez.  
Can SOMEbody help me out here?

My xorg file reads:

Section "Monitor"
    Identifier     "LM-965W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "LM-965W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Thanks much ..

Spoone

---

