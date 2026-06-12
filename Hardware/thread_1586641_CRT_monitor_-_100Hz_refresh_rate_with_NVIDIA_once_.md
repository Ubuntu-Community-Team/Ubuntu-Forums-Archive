---
title: "CRT monitor - 100Hz refresh rate with NVIDIA once again"
date: 2010-10-02
forum: Hardware
---

### Post by %zqMOA$@U97bJ£&amp; on 2010-10-02
I know that is a common problem for Ubuntu (and other distros) since I remember, but now I'm very angry about it and I think that I must solve this once for all!

I have installed Ubuntu 10.04.1, NVIDIA drivers etc and everything was ok but this morning Linux (nvidia-settings) again try to be smarter then I am.

I have EIZO FS F520 CRT and GF6150 SE (nv430). For 2 days everything was ok - there was 1024x768@100Hz. Today I see only 85Hz and "100hz" gone from option list. I see useless inter-something 67Hz instead.

When I go to /etc/X11/xorg.conf, I see:
> 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
**    Option         "metamodes" "1024x768_100 +0+0; 1024x768 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
But when I press [Save to X configuration] in NVIDIA panel and then [Show preview], I see:
> 
**# Removed Option "metamodes" "1024x768_100 +0+0; 1024x768 +0+0"**
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
REMOVED?? Why? Why nobody ask me? I don't agree - no way!

New graphic driver installed? Not by my hands.

First suspect: drivers update tool? No, I've turned it off in "starting applications" (or whatever it is called in English version).

Second suspect: system update tool? No - also turned off.

My questions are:
1. Who decided to remove? Why?
2. How to permanently override this settings and force 100Hz forever? 
I'm thinking about chmod 555 to xorg.conf, but I'm guessing that NVIDIA will ignore it and will set 85Hz anyway - just like today, right?
3. If I disable NVIDIA's tool in "starting applications", drivers would be working? I mean graphic accelerations and effect (compiz)? Will I be able to start Xorg or it just will hang when trying to set graphic mode?

This problem is present in Xorg&NVIDIA since I used first Ubuntu few years ego. I read many times about it, but (as showed above) NVIDIA panel always have different opinion about my settings and I never managed to solve it (every time backing to Windows). Now I'm tired of this - I want use my Linux without surprises every day.

---

