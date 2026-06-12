---
title: "MX900 button configuration problem"
date: 2008-10-14
forum: Hardware
---

### Post by SilverAdder on 2008-10-14
Im having a problem with my MX900 bluetooth mouse on my laptop running Hardy. Im trying to get the back and forward buttons working. My current xorg.conf section for the mouse looks like this: 
```
Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "7"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
```
As it is there, the wheel works but the back and forward buttons doesnt. If i swap the 4-5 and 6-7 pairs, so that ZaxisMapping is 6 7. then the back/forward buttons scroll and the wheel goes back and forward. Im not sure why it works when the weel is back/forward and the back/forward buttons are scrool, and doesnt work the other way around. Any ideas? I dont know what output you guys would need but just tell me and ill post it.

---

### Post by SilverAdder on 2008-10-15
bump

---

### Post by harmsma on 2008-10-19
Hi,

I'm using the MX900, and have used the scroll & back/forth successfully with both of these configurations (choose one):

```
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "ExplorerPS/2"
       Option          "ZAxisMapping"          "4 5"
       Option          "Emulate3Buttons"       "false"
       Option          "Buttons"               "11"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "evBits"        "+1-2"
        Option      "keyBits"       "~272-287"
        Option      "relBits"       "~0-2 ~6 ~8"
        Option      "Pass"          "3"
EndSection
```

---

