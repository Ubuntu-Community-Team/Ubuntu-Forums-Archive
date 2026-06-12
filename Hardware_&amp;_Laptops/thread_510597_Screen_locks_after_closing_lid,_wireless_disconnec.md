---
title: "Screen locks after closing lid, wireless disconnectivity follows"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by Sporkman on 2007-07-26
Xubuntu 7.04
Gateway Solo 9300
Netgear atheros-based wireless card

Screensaver set to "blank only", "lock screen" unchecked, power-saving features off.

Whenever I close the lid, then re-open, the computer asks for a password to unlock the screen. Furthermore, the wireless connectivity is patchy afterwards.

Anybody know how I can turn off the unwanted password verification, & whatever else it's doing to mess up the wireless?

:?

---

### Post by Sporkman on 2007-07-27
^^^

---

### Post by NilsE on 2007-07-27
Right click on power management icon and see what it says to do when  the lid is closed.  More than likely you are actually suspending the system.

If that is it then you need to either select "do nothing" or work on the password (probably in gconf) and the wireless by stopping it prior to suspend which you can search on here since I know there is a fix but don't remember it..

---

### Post by kaleido on 2007-09-20
Open a terminal, and run:
[INDENT] gconf-editor [/INDENT]
Under **Apps, gnome-power-manager:**
Uncheck **lock_on_blank_screen, lock_on_hibernate, lock_on_suspend.**

This should really be part of a Gnome control panel.

---

