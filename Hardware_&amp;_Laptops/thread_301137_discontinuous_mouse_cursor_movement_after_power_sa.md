---
title: "discontinuous mouse cursor movement after power save mode"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by xorwen on 2006-11-16
Hi,
I have logitech wireless mouse/kayboard set conected with USB port and PS/2. When Ubuntu goes back from power save mode (it's the default mode after screensaver, when screen is switched off ) the cursor movement starts to be very discontinuous even the buttons on keyboard have to be pressed longer to be catched by OS. It seems like bluetooth signal problem, but I've made a test with non-wireless USB mouse ant it's the same.
I'm using Egdy Eft and there was no problem with previous versions.

Here is a part of my Xorg.conf (I'd be glad to know what should be there for my logitech set):


```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "cz"
        Option          "XkbOptions"    "lv3:ralt_switch"
        Option          "XkbVariant"    "qwerty"
EndSection
```

---

