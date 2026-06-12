---
title: "No Keyboard or Touchpad 8.10 RC with an HPzt3000"
date: 2008-10-29
forum: Hardware
---

### Post by bibleman on 2008-10-29
I used the alternate install CD to install a command-line system. After doing updates I installed xorg. When I ran startx it came up fine except that the keyboard and the touchpad don't work.
I tried running dpkg-reconfigure xserver-xorg and it created a new xorg.conf but still there is no keyboard and touchpad. When I checked in the xorg.conf file I don't see a part about input devices which is usually there. 
These are the sections in xorg.conf
Device - my gfx card
Monitor
Screen
Anybody have any other ideas?

---

### Post by bibleman on 2008-10-31
I didn't think anyone would have an answer. I was never able to fix the problem and I resorted to doing a regular install.

---

