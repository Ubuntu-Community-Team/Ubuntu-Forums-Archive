---
title: "[SOLVED] Losing my screen settings on reboot"
date: 2008-08-21
forum: Hardware
---

### Post by HarrisonBP on 2008-08-21
So, it took me almost a day to figure out how to set my screen size and resolution correctly. The "Test" button in my displayconfig-gtk does not work properly and I did not save settings because when I tested screen things were all messed up.

Anyway, I now have it right.  That is, until I reset again.  Anytime I reset the resolution sets back to 800x600, it's not a big deal to change it every time I reboot, but it is such a pain.

Any help would be appreciated.

P.S. I have tried the disk button (save) in displayconfig's GUI, and after I restart, it too reverts back to 800x600.

---

### Post by pwnprog on 2008-08-22
sounds like it's not saving any of your changes to the xorg.conf file. try doing the same thing you were doing before, but this time as root. so if you were using displayconfig-gtk, this time go into terminal and type gksudo displayconfig-gtk . let us know how you make out.

---

### Post by HarrisonBP on 2008-08-23
Sorry, i never had the chance to try what you suggested, after logging off, and restarting a few times it just magically worked.

Strange wonderful thing this Ubuntu.

---

