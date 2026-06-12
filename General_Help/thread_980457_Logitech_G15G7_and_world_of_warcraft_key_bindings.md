---
title: "Logitech G15/G7 and world of warcraft key bindings"
date: 2008-11-12
forum: General Help
---

### Post by filthyphil on 2008-11-12
I have a Logitech G15 keyboard and a G7 mouse. I'm running wow with wine on ubuntu 8.10. I used xbindkeys and xmacro to bind left and right wheel tilt on the mouse to F9 and F10. The bindings work but in wow when I try to bind Alt + tilt, I get Alt+mouse button 4 or 5, and Alt+left tilt shows the ubuntu top and bottom panels for some reason. I already checked keyboard shortcuts and disabled all the F9/F10 ones.

For the keyboard, I have g15daemon installed and it seems to be working, except when I use xbindkeys -mk, the G buttons don't return any output.

It seems like something is intercepting my keys, but I have no idea what it could be.


The output of xbindkeys -mk is:

Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.

--- Press "q" to stop. ---
"(Scheme function)"
    m:0x10 + c:75
    Mod2 + F9
"(Scheme function)"
    m:0x10 + c:75
    Mod2 + F9
"(Scheme function)"
    m:0x10 + c:76
    Mod2 + F10
"(Scheme function)"
    m:0x14 + c:37
    Control+Mod2 + Control_L
"(Scheme function)"
    m:0x11 + c:50
    Shift+Mod2 + Shift_L
"(Scheme function)"
    m:0x18 + c:64
    Alt+Mod2 + Alt_L
"(Scheme function)"
    m:0x18 + c:64
    Alt+Mod2 + Alt_L
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 17 requests (17 known processed) with 0 events remaining.

---

