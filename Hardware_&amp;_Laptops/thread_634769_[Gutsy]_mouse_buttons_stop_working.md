---
title: "[Gutsy] mouse buttons stop working"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by rosco_pc on 2007-12-08
Hi,

The mouse buttons on my laptop, an Asus A8jr, recently stopped working when normally logging in. The mouse is working it self (can move the pointer), but no buttons are working.
If re-booting in safe mode the buttons are working, I've also tried different mice and none are working with this particular laptop, but they work on another A8JR.

Anybody a clue what is going on?

---

### Post by Yellow Pasque on 2007-12-08
How about looking at the mouse section in your /etc/X11/xorg.conf file? What does that look like?

---

### Post by rosco_pc on 2007-12-08
Got it solved, for some reason (I have not touched it), the 'Emulate3Buttons' option was set to "true". Setting that to "false" made it work again.

---

### Post by underdog512 on 2007-12-12
I have the same issue.  the emmulate3buttons was also true in my conf file but it has seemed to resolve my issue. any ideas?

---

### Post by rosco_pc on 2007-12-12
I have no idea, but there are more strange happening for me in Gutsy (Nautilus hanging, crappy video playback, problems with flash and so on). It does not seem to be one of the more stable releases.

---

