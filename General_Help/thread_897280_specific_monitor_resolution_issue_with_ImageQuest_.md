---
title: "specific monitor resolution issue with ImageQuest (Hyundai) Q770 low res in ubuntu"
date: 2008-08-22
forum: General Help
---

### Post by thabeatsociety on 2008-08-22
I have an ImageQuest (Hyundai) Q770 monitor and it only gets either 800 x 600 or 640 x 480 resolution.

I've read the thoroughly documented threads on this issue, but no fixes have worked for me.

I've followed:
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

and

[http://ubuntuforums.org/showthread.php?t=507777](http://ubuntuforums.org/showthread.php?t=507777)

and numerous others with no success.

I've also went to usr/share/applications and found Screen and Graphics, but it could not find my exact monitor type.  It does have ImageQuest Q910, but after just trying to select that model just to see if it's equally compatible with mine, it didn't work.  The model number isn't under Hyundai, which is in Screen and Graphic's list of monitor's too.  Ubuntu went into low graphics mode when I selected the Q910 monitor.

I also tried editing the xorg.conf file as such:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
	HorizSync       30-70
        VertRefresh     50-150
SubSection      "Display"
        Depth   24
        Modes   "1024x768" "800x600" "640x480"
EndSubSection

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Generic Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Any ideas?
:confused:

---

