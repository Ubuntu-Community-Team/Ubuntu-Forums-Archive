---
title: "Razer diamondback buttons"
date: 2011-03-22
forum: Hardware
---

### Post by Zirts on 2011-03-22
Hi,


Basicly my Xorg.conf has this entry for my mouse:
```

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Resolution" "1600"
       Option "Buttons" "9"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "one page back" "4"
       Option "one page forward" "5"
EndSection

```

With this I get my mouse wheel working and the 2 main buttons working and the 2 left side buttons,  but my prob is that is it possible to get the 2 right side buttons binded to something like numboard 3  or so also?

---

