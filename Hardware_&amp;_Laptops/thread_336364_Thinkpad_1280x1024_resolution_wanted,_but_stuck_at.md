---
title: "Thinkpad 1280x1024 resolution wanted, but stuck at 1024x768"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by MMoose on 2007-01-11
Hi all, 

I have a Thinkpad T42, with an ATI video card in it, that is docked most of the time. The LCD screen that is attached is capable of 1280x1024, and so is the card, based on the fact that it works at 1280x1024 in windows. :)

I'm having trouble making Xorg realize that it's capable of displaying at 1280. Can anyone help?

Here is my xorg.conf from /etc/X11. (with the non-pertinent bits taken out -- if you need them in please tell me!)

I've also attached the output of my /var/log/Xorg.0.log as Xorg.0.log.zip. I can see where the problem is (I think), but I'm not sure how to fix it! This error seems to be the reason:

(WW) RADEON(0): Mode 1280x1024 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768

But I know that it's possible to use 1280x1024!

Thanks for any help!
MMoose


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "XaaNoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by filippod on 2007-01-11
See this thread:

[http://www.ubuntuforums.org/showthread.php?t=336165](http://www.ubuntuforums.org/showthread.php?t=336165)

and apply the changes from Example 2 too (but be sure to put values which are correct for your monitors - you should find the specifications on the supplier's websites).

To edit xorg.conf use sudo: for example:```
[FONT="Courier New"]sudo gedit /etc/X11/xorg.conf[/FONT]
```

P.S.
If this should fail, if you search further on ubuntuforums there are other posts detailing other cases.

---

### Post by MMoose on 2007-01-12
Thank you so much! That led me to the right place to look! All I needed to do was to specify the refresh rates for my monitor (LG L1710S), and the settings for 1280x0124 kicked in! Thank you!

---

