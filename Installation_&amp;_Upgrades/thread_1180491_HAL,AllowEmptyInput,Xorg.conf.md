---
title: "HAL,AllowEmptyInput,Xorg.conf"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by raj1679 on 2009-06-06
Recently installed Ubuntu 9.0.4 on Acer Travelmate 4052 laptop. The Keyboard, Pointer pad on my laptop are unusable when the X server is started. When checking xorg.conf realized that the devices are not mentioned in the conf file. Even after mentioning relevant sections in the conf file, the Xorg.0.log says that since AllowEmptyInput is on, the keyboard,pointer will be disabled. Please suggest.

---

### Post by raj1679 on 2009-06-08
Keyboard and Mouse did not work after the Screen got loaded. I checked the /VAR/LOG/Xorg.0.log for errors only to find that keyboard and mouse are not getting loaded. After numerous trials the following worked for me. Now I am able to use the X environment.

Please try..

Add the following in the current xorg.conf before the sections which are already present.

Section "ServerFlags"
     Option "AllowEmptyInput" "off"
EndSection

Section "InputDevice"
     Identifier "Keyboard"
     Driver "kbd"
EndSection

Section "InputDevice"
     Identifier "Mouse" 
     Driver "mouse"
EndSection

---

