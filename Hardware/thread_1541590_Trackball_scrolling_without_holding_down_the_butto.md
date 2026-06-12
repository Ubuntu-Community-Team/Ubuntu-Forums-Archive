---
title: "Trackball scrolling without holding down the button?"
date: 2010-07-29
forum: Hardware
---

### Post by fireonyx on 2010-07-29
I have a logitech Marblemouse trackball.  I found the settings to allow me to hold down the small button and then scroll.  This is the edit to xorg.conf
```
Section "InputClass"
        Identifier "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "ButtonMapping" "1 8 3 4 5 6 7 2 9"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "8"
        Option "ZAxisMapping" "4 5"
        Option "XAxisMapping" "6 7"
        Option "Emulate3Buttons" "false"
EndSection
```

It is a pain to hold down the small left button all the time when scrolling.  I was wondering if there was a way to make this button "sticky".  Click it once, scroll on.  Click it again, scroll off.  It would even be better yet if you could hold down the button for more then a few seconds, and it wouldn't sticky for just short scrolling.

Any thoughts on how to accomplish this?

---

### Post by fireonyx on 2010-07-30
Bump

---

