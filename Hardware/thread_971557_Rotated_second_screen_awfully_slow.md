---
title: "Rotated second screen awfully slow"
date: 2008-11-05
forum: Hardware
---

### Post by RealMurphy on 2008-11-05
Hi all,

I'm working on a Thinkpad T43p which has a  ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80) graphics card. Next to the laptop is a nice TFT which can be rotated and would be great to use this feature.

However, I never succeeded with fglrx and currently trying the 'radeon' driver and with 

xrandr --output VGA-0 --right-of LVDS --auto 
I get already the extended desktop but when I rotate that via xrandr it works, but is incredibly slow, e.g. I can easily follow the screen update whenever a terminal updates.

My xorg.conf is pretty much the same as it's generated automatically I only added lines to support the larger virtual desktop:

> 
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
           Depth                24
           Modes                "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           Virtual              2880 1280
       EndSubSection

EndSection


Any idea how to speed this up?

Cheers

Carsten

---

