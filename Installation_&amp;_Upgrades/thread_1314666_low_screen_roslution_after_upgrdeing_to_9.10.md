---
title: "low screen roslution after upgrdeing to 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by raspotin on 2009-11-04
hey guys
i've just upgraded my 9.04 ubuntu to 9.10
by an alternative cd image
but the surprise that the resolution become 800*600
with no other options although in 9.04 it was 1024*768
i tried xrander -s 1024*768
but the result was

> Size index 1024 is too large, there are only 2 sizes
i added this to xorg.conf and restarted xserver but in vain

> 
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection


i tried this

i tried to add new mode by xrandr
but at the end when i typed

> xrandr --addmode lvcd1 1024x768_60.00
the result was

> 
xrandr: cannot find output "lvcd1"
by the command lspci | grep VGA
i get this

> 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
so i think that there is no problem with the driver

what can i do ?!!

---

