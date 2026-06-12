---
title: "For those of you who are having mouse button problems"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by wilsonisme on 2006-09-24
I have a Razer Copperhead (although this may work fine for other kinds of multi button mice) and nothing was working, then I tried s3ppel's xorg.conf mouse section and it worked like a charm. Good luck!


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "Resolution" "1600"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection

---

