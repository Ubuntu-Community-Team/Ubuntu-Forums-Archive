---
title: "Lock Screen with Super L issues"
date: 2008-11-17
forum: General Help
---

### Post by phikapjames on 2008-11-17
To start with, in 8.04 I had it setup through Gnome's Keyboard Shortcuts so that I only had to hit the Super L (Windows Key) by itself to lock my screen.  Once I upgraded to 8.10 it no longer works.  The shortcut still exists in the Keyboard Shortcuts.  I switched it with a different combination and it works, but if I changed it back to Super L it doesn't work anymore.

From another thread, it suggested using xmodmap to removing the binding, so now xmodmap displays:

xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4      
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

Notice mod4 no longer has the Super L combination, but I'm still not able to user the Super L to lock the screen.  Any help with this issue will be greatly appreciated.

---

### Post by Malac on 2008-11-17
This is because compiz grabs this key so any press of Super_L is interpreted as part of a key combo for compiz effects.
I had my menu setup to open on Super_L but had to change it to <Shift><Super_L> it was either this or go through every compiz setting unsetting the Super keys

Hope this helps.

---

