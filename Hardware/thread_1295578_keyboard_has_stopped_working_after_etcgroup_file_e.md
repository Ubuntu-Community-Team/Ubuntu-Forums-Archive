---
title: "keyboard has stopped working after etc/group file exploded"
date: 2009-10-19
forum: Hardware
---

### Post by Birdomuerto on 2009-10-19
Yesterday my computer stopped working... I traced the problem to the /etc/group file... which had somehow gotten completely wiped. I copied a few examples to make a new one and I can get back to the login screens for the GUI...

while I'm able to use my keyboard in the 'safe' command screen mode to edit files, etc., once the GUI comes up the keyboard and mouse are disabled.

Connections for keyboard and mouse are PS2.  I made a wild guess and disabled USB input in BIOS... no luck.

Any ideas?  Everything had been working fine for months.

---

### Post by Dark_Stang on 2009-10-19
Could be your /etc/X11/xorg.conf file...?

---

### Post by G-Freshman on 2010-04-08
> **Dark_Stang said:**
> Could be your /etc/X11/xorg.conf file...?

I have the same problem but I dont have x11 folder
where i can find xorg.conf

---

