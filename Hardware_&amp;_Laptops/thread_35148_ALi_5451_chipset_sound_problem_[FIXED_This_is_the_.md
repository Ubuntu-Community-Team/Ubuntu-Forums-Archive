---
title: "ALi 5451 chipset sound problem [FIXED: This is the solution]"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by nmorse on 2005-05-17
For those of you with an ali5451 chipset card, sound will not work by default. There is actually a problem with a name mismatch between Jack Sense and External Amplifier. To fix this, simply disable both in a mixer, like alsamixergui or kmix. After that, sound should work perfectly.

This fix may work for other sound cards who give an error relating to Jack Sense or External Amplifier.

Have fun with your now working sound.

---

### Post by Rollerbob on 2006-02-18
I've seen this solution in a number of places. However, I'm running Breezy and when I run Alsamixer there is no Jack Sense option to disable. External Amplifier is there but no Jack Sense. The same is true if I run the Gnome sound mixer. I've been trying to get the sound working on my Toshiba Portege 4010 (with Ali 5451 chipset) for weeks, please help!

---

