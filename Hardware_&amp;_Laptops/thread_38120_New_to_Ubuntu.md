---
title: "New to Ubuntu"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by datchison on 2005-05-30
I am new to Ubuntu and everytime it starts it gives me this problem

Attention out of Range
H:29.1 Khz
V:55.5Hz

So i believe its trying to load Gnome
So i try to use (Ctrl+ALT and Backspace) it goes to the prompt then shows the same message everytime. So i don't know what to do????

---

### Post by ltmon on 2005-05-30
It's a monitor sync problem.  Linux probably hasn't detected your sync rates correctly.

At a guess (I'm no guru) you should:

1. Press ctrl-alt-F1 to get a text only terminal
2. login

> sudo nano /etc/X11/xorg.conf

Loook for the section entitled 

Section "Monitor"

In there is the entries for the refresh rates and horizontal sync.  Set these to something like the settings recommended by your monitor manufacturer.

Then go back to the graphical display (ctrl-alt-F7) and restart X again (ctrl-alt-Backspace)

Make sure you back up xorg.conf before trying this!

Hopefully someone with more of a clue can chime in if I'm wrong.

Cheers,

L.

---

