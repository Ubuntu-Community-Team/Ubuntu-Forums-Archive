---
title: "[SOLVED] dell latitude c600 resolution issues"
date: 2008-11-22
forum: Hardware
---

### Post by dmatthys on 2008-11-22
Hello, I am running a Dell Latitude C600 with an ATI Mobility M3 and can not change past resolution 800x600 by System > Preferences > Screen resolution i have only been using ubuntu for about a week so im still learning and so far has been a pretty good experience untill now so after days of searching and trying things i decided to post here quick run down

reconfigure xserver-xorg did not work

manually configured xorg.conf and this is what i got however it still doesnt fix the problem although it did fix the problem of ubuntu running in low graphics mode that was a releif 

Section "Device"
 Identifier "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
 Driver "ati"
 BusID "PCI:1:0:0"
     # External monitor is a viewport into the panel
            Option "MetaModes" "1024x768-1280x1024"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
 Monitor "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth 1
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection
EndSection

any ideas would be greatly appreciated if any other information is needed just ask and please include instructions on how to obtain it as i said only been using this os for a week total noob

---

