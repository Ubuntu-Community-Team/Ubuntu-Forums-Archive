---
title: "Apple Mighty Mouse stopped working in Heron"
date: 2008-05-16
forum: Hardware
---

### Post by yoonkit on 2008-05-16
I managed to get the Mighty Mouse working with horizontal scrolling using evdev on Feisty Fawn. After installing Hardy Heron, my xorg settings did not work: meaning on bootup in X, using the same settings, the mouse was not registered and could not move.

Here is the settings for my Feisty setup:

[http://yoonkit.blogspot.com/2007/09/mighty-mouse-wired.html](http://yoonkit.blogspot.com/2007/09/mighty-mouse-wired.html)

```
Section "InputDevice"
Identifier "MightyMouse"
 Option "CorePointer"
 Driver "evdev"
 Option "Name" "Primax Electronics Apple Optical USB Mouse"
 Option "HWHEELRelativeAxisButtons" "7 6"
 Option "Buttons" "8"
 Option "Buttons" "9"
EndSection
```

I am now using the "mouse" driver, which doesnt support horizontal scrolling.

Anybody got any ideas?

Thanks.

yk.

---

