---
title: "Numpad is not working, no numbers"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by sagara on 2007-11-18
After a fresh smooth installation of Gutsy, I've noticed that I've lost my numeric keypad.

The ** numlock** key doesn't work, no on or off, its just always off.  This means that the numbers ONLY work as arrows.

I was working with feisty before without a single keyboard problem.  Any ideas why this is happening?  I never noticed how complicated things get without a numpad.

extract of my **xorg.conf** file
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

```

---

### Post by gwoodard on 2007-11-18
Similar Problems...In a game sometimes the numbers above the letters don't work and the keypad works (even though i have to press the numbers really hard)

---

