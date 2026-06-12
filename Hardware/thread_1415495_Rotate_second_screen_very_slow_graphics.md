---
title: "Rotate second screen: very slow graphics"
date: 2010-02-24
forum: Hardware
---

### Post by dehmann on 2010-02-24
I am using two monitors. When I rotate the second one left (so that it is in portrait mode) it becomes incredibly slow! To be precise, moving a window around on that second screen becomes so slow that I can watch it as it draws row by row.

To rotate, I select "Rotation: left" in System->Pref.->Display. Before that, I set an appropriate virtual size in my xorg.conf. Below is the complete xorg.conf file. 

The screen resolutions of my two screens are 1280x1024 and 1680x1050. I'm rotating the second one, so that the virtual size becomes 1280+1050=2330, and the height becomes 1680. 

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2330 1680
                # Virtual       2960 1050                                       
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "RandRRotation" "yes"
        Option          "XRandR" "true"
EndSection

When I go in System->Pref.->Display again and set Rotation to "normal" it writes the virtual size 2960x1050 to xorg.conf, and graphics performance is back to normal.

What can I do? I really want that 2nd screen to be in portrait mode, but if it's that slow it is unusable.

I am using Ubuntu 9.10, my graphics card is ATI Radeon R300, and I'm using the ati driver. 

Rotate right gives the same slow behavior. BTW, the slowness on rotate only occurs if two screen are used. If one is turned off then the remaining one works fast even when rotated.

---

### Post by pilpi on 2010-07-05
Same problem here. IBM Thinkpad T41 and Samsung 940B. 
Before 10.04 it did not work at all though, so this is already a hint better :P.

---

### Post by doublee on 2010-11-15
Same problem here.

Dual-monitor works smoothly unless any of the screens are rotated. Rotating both doesn't help either - graphics become incredibly slow...

---

