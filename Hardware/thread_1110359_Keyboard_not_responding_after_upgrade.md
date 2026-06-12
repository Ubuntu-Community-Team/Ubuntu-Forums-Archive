---
title: "Keyboard not responding after upgrade"
date: 2009-03-29
forum: Hardware
---

### Post by coacharnold on 2009-03-29
There were some xorg upgrades this past week or so and since nice my old school ps2 keyboard doesn't work...   It works if I drop down into a terminal session but not in x ....  in fact it even works at the log in prompt..  Below is a copy of my xorg.conf file ....  I un-commented the sections that had to do with the keyboard and the mouse thinking it might do something ... but it still doesn't ///   Is there a hal setting thats changed or something 



Does anybody have any idea what this is??

I'm running Intrepid with KDE4.2 

Thanks 
Tim 

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Option          "AddARGBGLXVisuals"     "True"
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

---

### Post by coacharnold on 2009-03-29
OK ....  it seems after some trial and error that the problem is intermittent .... sometimes the keyboard works... (I.E. right now I'm typing on it) and sometimes it doesn't.

anybody have any thoughts????

T

---

