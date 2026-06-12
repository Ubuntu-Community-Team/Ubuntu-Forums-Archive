---
title: "Mouse with exra buttons"
date: 2008-05-03
forum: Hardware
---

### Post by IbeeX on 2008-05-03
Hello

in my dapper I managed to configure extra mouse buttons in my xorg configuration with 

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Butons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

and it worked for firefox as back and forth buttons, after update to hardy this is no longer working is it due to xorg 7.3 or firefox 3 ? or maybe something else.

thx

---

