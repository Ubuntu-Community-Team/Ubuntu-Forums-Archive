---
title: "Unique Thumb Button Problem"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by Doublerob7 on 2007-07-23
I'm using a Wireless Intellimouse Explorer 2.0 and i've tried just about every tutorial in existence to try to get my thumb buttons to work. would someone please help me understand what's going on here...

i've installed and removed both imwheel and xbindkeys, in attempts to start from scratch when one fails to work, so something might be fuxed in some file that i edited and forgot about =\

here's my xorg.conf section:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option	   "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

when i run XEV and press the 'back' thumb button, it outputs this:
```
ButtonPress event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171903617, (176,152), root:(373,343),
    state 0x10, **button 4**, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171903623, (176,152), root:(373,343),
    state 0x810, **button 4**, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171903626, (176,152), root:(373,343),
    state 0x10, **button 6**, same_screen YES
```

and this for the forward thumb button:
```
ButtonPress event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171915897, (176,152), root:(373,343),
    state 0x10, **button 5**, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171915899, (176,152), root:(373,343),
    state 0x1010, **button 5**, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x186, subw 0x0, time 171916170, (176,152), root:(373,343),
    state 0x10, **button 7**, same_screen YES
```

apparently X is interpreting my thumb buttons as 'wrong-button' clicks and then as 'correct-button' releases. wtf is going on?

---

