---
title: "Ctrl and Alt"
date: 2008-06-22
forum: Hardware
---

### Post by novio8 on 2008-06-22
Hi,
I would like globally swap my Ctrl and Alt Key.
Ubuntu 8.04 on HP Compaq 6820. Instal went ok, had some 
problems with WLAN and Graphical card, now everything works.
My first Linux expirience.

Please advise
Mario

---

### Post by damphoud on 2008-06-22
You prob need to look into /usr/share/X11/xkb/symbols, note ctrl, us, altwin. What you need to change in there, I'm not sure, but its a start.

$ cd /usr/share/X11/xkb/symbols     (brings you to symbols dir)
 
$ ls                                (will show you files inside)

$ sudo gedit us &                   (edits basic us keyboard layout)


I'll keep looking, see if I can find something.

---

### Post by damphoud on 2008-06-22
In System -> Preferences -> Keyboard, tab Layout, button Layout Options... under Ctrl key position, you can select right ctrl key works as right alt. But you need them switched around and done to the left side too?

---

### Post by novio8 on 2008-06-22
thank you damphoud,fast reply
I tried in Keyboard Layout Preferences, but I can't achive
this simple setting, it should be easy.
Mario

---

### Post by damphoud on 2008-06-22
I tried to play around with the "ctrl", but I ran into some errors... I'm not too sure, maybe do some researching on google? Maybe they should make a easy and simple ui program to change the keyboard, would be cool.

---

