---
title: "[SOLVED] Wacom Intuos3 Back/Forward Buttons?"
date: 2008-12-20
forum: Hardware
---

### Post by chisayne on 2008-12-20
OK with the help of the guides and reading through other posts I've managed to get my Wacom tablet working, mouse and all. The only problem is the Back/Forward side buttons on the mouse don't seem to take the settings I'm giving them. Basically I want them to be back/forward in Firefox (Alt+left and Alt+right respectively). I've tried with both wacomcpl and xsetwacom to set Button5 to alt+left and Button4 to alt+right, but they end up for some reason sending alt+4 and alt+6 (firefox jumps to the 4th tab when I press the left button, 6th tab when I press the right). Anyone have any ideas that might help?

running ubuntu 8.10, wacom driver 0.8.1.4 (version packaged with intrepid)

Code I am using to set the keystrokes:
```
xsetwacom set cursor button4 "key core alt right"
xsetwacom set cursor button5 "key core alt left"
```

Any help would be greatly appreciated.

---

### Post by chisayne on 2008-12-20
Silly linux noob didn't try turning off numlock >.>

---

