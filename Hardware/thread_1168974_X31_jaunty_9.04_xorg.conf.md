---
title: "X31 jaunty 9.04 xorg.conf"
date: 2009-05-24
forum: Hardware
---

### Post by venky80 on 2009-05-24
Could some ibm thinkpad X31 user post their xorg.conf i am not able to make it work in Ubuntu

---

### Post by dan_kent on 2009-06-03
Here's my X31 xorg. A default install of Jaunty works for me but this xorg gives me much smoother performance and scrolling; 


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#       SubSection "Display"
#               Virtual 2960 1050
#       EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelDFS" "on"
#        Option          "AccelMethod"  "EXA"
        Option          "MigrationHeuristic"  "smart"
        Option          "EnablePageFlip"  "on"
        Option          "EnableDepthMoves"  "on"
#        Option          "ColorTiling"  "on"
#       Option          "DisplayPriority"  "HIGH"
#       Option          "DepthBits"  "24"
#       Option          "SubPixelOrder"  "RBG"
       Option          "DRI" "off"
        Option          "FBTexPercent"  "0"
        Option          "RenderAccel"  "on"
EndSection

Section "ServerFlags"
        Option          "DontZap"       "off"
EndSection

---

