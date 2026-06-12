---
title: "up arrow activates gnome-screenshot"
date: 2008-11-20
forum: General Help
---

### Post by Locutus_of_Borg on 2008-11-20
using compiz standalone, for some reason the up arrow takes screenshots, and my home key no longer works.  left right and down work normally as does end, but up and home are somehow affected.  Any idea?


Well, got it to stop taking screenshots by going to ccsm > general options > commands and deleting the mention of screenshots, but the up arrow now no longer does anything as does Home

---

### Post by Locutus_of_Borg on 2008-11-20
nano /etc/X11/xorg.conf
change keyboard driver to evdev
comment out all mention of xkb
working normally again

i should *really* try out more things before making threads about them...but maybe someone will have this same problem and find the solution quicker than I did.

---

### Post by brianfinley on 2008-12-09
Actually, I'm glad you posted this thread, as it solved my issue with intrepid right away.

Thanks!

---

