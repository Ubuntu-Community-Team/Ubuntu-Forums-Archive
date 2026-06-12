---
title: "problems with gnome desktom and 2 screens(Gutsey)"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by pinan on 2008-02-25
Just been trying to setup a sony laptop with an addional screen connected to it.  I want the 2nd screen to appear to be 2nd monitor.

After some fun with /etc/X11/xorg.conf, xdypinfo now reports two screen, actions stations I through.  Butr on loggin in with the Gnome GL dekstop, only the laptops flat pannel worked.  Its possible to move the cursor between the two screen.

After trying many werid settings, I just happen to login in using the "failsafe" mode, shock horror both screen started working, both lit up, its possible to invoke application on the 2nd screen from the toolbar.  So I must have a problem with the desktop settings,  I have tried login in with KDE, it behaves in the same way as Gnome, only one screen works.  I have disabled all off the effects that I could find for the compiz window manager, but alas it did'nt help.

Anybody got any clues as to what the problem could be ?

The attached file is a copy of my machine /etc/X11/xorg.conf, ( its not the work of art that it could be, but I want to get this problem sorted first)

---

