---
title: "Touchscreen calibration doesn't work at 800x600"
date: 2008-08-08
forum: Hardware
---

### Post by craftybones on 2008-08-08
Hello,

I have an ELO touchscreen and this is the relevant post from my xorg.conf

Section "InputDevice"   
        Identifier      "touchscreen1"
        Driver          "elographics"
        Option          "screenno" "0"
        Option          "Device" "/dev/ttyS0"
        Option  "MinX"  "463"
        Option  "MaxX"  "3667"
        Option  "MinY"  "548"
        Option  "MaxY"  "5578"
        Option          "UntochDelay" "3"
        Option          "ReportDelay" "1"
EndSection


Section "ServerLayout"  
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "touchscreen1"  "SendCoreEvents"
EndSection


The config works great for 1024x768 but the touch screen doesn't act well under 800x600. The cursor aligns at the top left hand corner, but the further you go towards the right or bottom, the further the cursor gets away.

I have tried several calibration tools(touchcal, calibrator etc) and elo's own tool that they provide for Dos, under both Dos and dosbox. But no luck.

Has anyone here had a similar problem? Does anyone know what might be wrong? Can you please assist me? 

Thank you,

Crafty

---

### Post by craftybones on 2008-08-11
Hello,

Does anybody have a solution/suggestion?

Thank you,

Crafty

---

### Post by craftybones on 2008-08-11
Hello,

This is a very important requirement for me to have done. I would appreciate any help on this matter. Even a pointer pointing me in a relevant direction.

Thank you,

Crafty

---

