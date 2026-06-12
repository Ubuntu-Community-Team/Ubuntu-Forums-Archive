---
title: "Fixing display rotated left"
date: 2008-10-05
forum: General Help
---

### Post by jonathonblake on 2008-10-05
All:

I accidentally configured the display to be rotated left.

None of the tool bars are visible in the part of the screen that is displayed.  By random clicking, I can locate the application menu, but only the top half.  Random clicking hasn't produced the preferences menu.  :(

I looked for configuration files that could be manually edited, to change it, but found nothing that looked right.   Reading the various threads, and poking thru the configuration files, I haven't found anything that points to something being fixable using a text editor.    :(

System setup:
1 monitor (Samsung 15th LCD)
on board graphics
AMD 64 bit chip.(Athalon dual core something or other.)
Ubuntu 7.04 hardy (64 bit version)
8 GB RAM

xan

jonathon

---

### Post by Rhubarb on 2008-10-05
Press Alt + F2, and enter this in:
```
gnome-display-properties
```
This will bring up the Monitor Resolution Settings program (that's found in System --> Preferences --> Screen Resolution).
This allows you to change the rotation back to normal.


Alternatively you can press Alt + F2, then enter in:
```
xrandr -o normal
```
Which will orient the screen back to normal automatically.


If you wish to access the Applications / Places / System menu via the keyboard, press Alt + F1, then use your cursor keys to navigate around.

---

