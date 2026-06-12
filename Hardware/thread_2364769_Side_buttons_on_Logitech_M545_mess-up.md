---
title: "Side buttons on Logitech M545 mess-up"
date: 2017-06-27
forum: Hardware
---

### Post by joost102 on 2017-06-27
Hello,

I am quite new here, but feel i need some help. I run Ubuntu 16.04 and have a Logitech M545 mouse with 2 side buttons. I really would like those to work, by assigning a key to them. In this case one button linked to "l" and the other to "k".

I have been working on this in the past, and I don't remember how, but it seems i have messed up the assign settings somehow. Somehow I have assigned key 133 and key 40 at the same time on one of the side buttons, and key 133 to the other. I would like to get those deleted and use xbindkeys to set the right keys to the buttons.

When using the xbindkey config I can see one button is Mod4 + Super_L and other is Mod4 + d. That last side key actually produces a "d" when i press it, but not very reliable.

Can anyone help me out here?

Thx

---

### Post by efflandt on 2017-06-28
I have not used "xbindkey" and apparently do not even have it on my system. If you are using regular Ubuntu I would try undoing that and installing/using CCSM (CompizConfig Settings Manager). That has a gui that under General > Commands allows you to set a list of commands (which could be single keys) to assign to key combinations or mouse buttons.

My Logitech MX Master mouse has a hidden button on its foot under my thumb (separate from side mouse buttons 4 & 5) which only sends keycode for Ctrl+Alt+Tab. If accidentally hit during an intense game (even full screen) that tended to either switch to a different window or to desktop (annoying). So I used a different part of CCSM under Desktop > Ubuntu Unity Plugin > Switcher to use easy to remember Ctrl+Alt+Home for the window switcher instead of Ctrl+Alt+Tab which effectively deactivates the foot mouse button that sends only that keycode. But I can still usually use the Ctrl+Alt+Home I assigned to the switcher if even a full screen X program hangs (or if all else fails, Ctrl+Alt+F1 to get to a vt).

---

