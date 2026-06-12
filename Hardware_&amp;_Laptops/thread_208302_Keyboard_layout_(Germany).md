---
title: "Keyboard layout (Germany)"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by mamato on 2006-07-03
Hi all, I have a laptop HP pavilion DV5162ea with german keyboard. At the install process, all of the keys are correctly mapped. Suddenly, maybe because I change the keyboard settings, I can't longer use the > key. 
Can anybody tell me how i fix this? I need it, because I work with terminal most of the time.

---

### Post by Rollmops on 2006-07-03
My "/etc/Xorg/xorg.conf" looks like this:

```

[...]
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
EndSection
[...]

```

And in "gnome-keyboard-properties" 
Modell: Generic 105-key (Intl) PC
Belegung: Germany eleminate dead keys

---

### Post by mamato on 2006-07-05
Thank you very much, now it's work :D

---

