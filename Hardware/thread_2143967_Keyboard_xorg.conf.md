---
title: "Keyboard xorg.conf"
date: 2013-05-10
forum: Hardware
---

### Post by marcosmp on 2013-05-10
Hi,

I am trying to configure a unknow keyboard Staco system keyboard M713116, but i dont know what file i need to change, i tried to configure a generic keyboard in xorg.conf just like this:

Section "InputDevice"
Identifier   "Generic Keyboard"
Driver       "kbd"
Option       "CoreKeyboard"
Option       "XkbRules"      "xorg"
Option       "XkbModel"      "pc105"
Option       "XkbLayout"     "us,sk"
Option       "XkbVariant"    ",qwerty"
Option       "XkbOptions"    "grp:menu_toggle,grp_led:scroll"
EndSection

Is there any different file to change?

---

