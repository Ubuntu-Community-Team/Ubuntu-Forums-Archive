---
title: "Panel has Gone West - 8.10"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Muzzargh on 2009-03-12
Ooops.  I have just installed 8.10, standard install, just put the CD followed the steps....all good so far.

Rebooted, logged in and liked what I saw :P

Task bar (panel) at the top, dragged it to the bottom to see what it would look like and the bar went blank (white) except for the two screen and trash icons on the right.   Dragged it back to the top and it remained the same.   Stupidly I right clicked and selected Delete panel.

Now I have a blank desktop :(

Nothing has worked to get it back yet so I'm just going to reinstall; but it would be nice to know how to get it back in future if it happens again.

Murray

---

### Post by kidux on 2009-03-12
Hit ALT+F2, then type gnome-panel. See if that brings it back.

---

### Post by Muzzargh on 2009-03-12
Cool I'll try that tonight, thanks for the help. :D

---

### Post by Muzzargh on 2009-03-13
All I get is "Cannot open Display"?

I tried the help and it says --display=DISPLAY   X display to use.

So I tried gnome-panel --display=1

and I get cannot open display so I guess it's a syntax or keyword thing.

Appreciate your help.

---

### Post by Muzzargh on 2009-03-13
OK so it helps if I actually READ the instructions and just press Alt+F2 without adding the CTRL button as well.

Anyway it didn't work either.

So I did some more searching and found this:

Press ALT+F2 and in the run dialog box, type gnome-terminal

In the terminal type

[INDENT]gconftool-2 --shutdown 

rm -rf ~/.gconf/apps/panel

pkill gnome-panel[/INDENT]

That’s it!

Thanks to albertsiow
[http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/](http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/)

---

