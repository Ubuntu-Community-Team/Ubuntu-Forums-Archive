---
title: "Using the old X11 cursor theme ??"
date: 2008-09-11
forum: General Help
---

### Post by pop69er on 2008-09-11
Hey,

I'm somewhat kinda new to the Linux operating system stuff, but I'm running Ubuntu 8.04, and I want to know how to use the old original generic X11 cursor theme found in really old versions of Solaris and stuff .. like Solaris 7, 8 .. ect .. plain small black cursor, and the arrow and the wrist watch .. like the really old stuff .. is it possible?

---

### Post by Infinite Indefinite on 2008-09-11
Have you placed the theme in ~/.icons ?

If so then you can navigate to System > Preferences > Appearances.  Select Customise and then click the Pointer Tab.  Your cursor should be in the list.

---

### Post by kerry_s on 2008-09-11
> **pop69er said:**
> Hey,

I'm somewhat kinda new to the Linux operating system stuff, but I'm running Ubuntu 8.04, and I want to know how to use the old original generic X11 cursor theme found in really old versions of Solaris and stuff .. like Solaris 7, 8 .. ect .. plain small black cursor, and the arrow and the wrist watch .. like the really old stuff .. is it possible?

i know if you uninstall all the added cursors it will go back to the core.
or
you can try changing /usr/share/icons/default to "core", not sure, i don't have any cursors installed so i actually am using the 1 you want.

---

### Post by aswinbabuk on 2010-03-26
I was also interested in doing this and it took me some time to figure out how to remove all cursors from your system.
1] Open Synaptic Package manager
2] Search for cursor or themes
3] Uninstall everything that you think belong to a cursor
4] Restart your window manager (Gnome, KDE, XFCE or whatever)

---

