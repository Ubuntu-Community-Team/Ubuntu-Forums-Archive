---
title: "Detecting mouse type"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Kjella on 2007-12-14
I'm running Kubuntu 7.10 using an IntellMouse Explorer (don't know exact make), and in the default install the side buttons are not working as they should. Actually I have already found the solution, it's to edit xorg.conf and replace
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```
with
```
Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "mouse"
        Option         "CorePointer"
        Option         "Device" "/dev/input/mice"
        Option         "Protocol" "ExplorerPS/2"
        Option         "Emulate3Buttons" "true"
        Option         "Buttons" "7"
        Option         "ZAxisMapping" "4 5"
        Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```
What I'm looking for is "Where do I tell someone about this so it gets fixed? (They'll probably want some kind of USB ID as well I'd guess). Hacking xorg.conf to get my configuration working is not a problem for me, but this I think is rather basic functionality lacking for non-technical users. Even if there 's no autodetection I can't imagine there being more mainstream mouse models than that you can just use a lookup table.

---

