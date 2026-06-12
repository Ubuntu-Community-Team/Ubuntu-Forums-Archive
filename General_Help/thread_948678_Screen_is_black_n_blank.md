---
title: "Screen is black n blank"
date: 2008-10-15
forum: General Help
---

### Post by srujan on 2008-10-15
guys i'm new to linux....n i tried to use the desktop effects....but i fiddled around with addin widgets n now my entire is blank n black....i can flip my screen....but i cant do anything else......so how do i get it back to the original form.....

---

### Post by brianfreytag on 2008-10-15
Can you get a terminal open and post the output of /etc/X11/xorg.conf ?

It's a possibility this got corrupted or messed up in your course of modifying.

One thing you can try if you can't get ANYTHING to come up on the screen is at the login screen at the bottom left there is an option for Sessions, select "Gnome."  If THIS doesn't work, go back to the login screen (ctrl + alt + backspace) go back to sessions and select Fail-Safe Gnome.

This should put a simple xorg.conf into play and it should let you get into your desktop so you can open a terminal to record the output of the xorg.conf.

Also, it is usually a wise decision to give the following information when posting a problem:

Ubuntu version (8.04/8.10)
Gnome or KDE?
Computer specs (graphics card especially)

---

### Post by srujan on 2008-10-15
thanx a lot....i'll try it out...

---

