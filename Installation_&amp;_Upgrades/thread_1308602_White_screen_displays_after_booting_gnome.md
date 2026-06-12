---
title: "White screen displays after booting gnome"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by geoffm on 2009-10-31
I upgraded my Dell XPS M1330 to 9.10. Boots fine, I see a splash screen, I see the usual black background with the grey lines of the gnome panels on top and bottom of the screen but after a few seconds then the screen gets all white. I only see the cursor on a white background. Gnome is runnnig fine, I can click my panel launchers and I know it opens an app. Using keyboard shortcuts I can get to the shell but don't see a thing. I figure it might be compiz that doesn't work anymore? How can I disable compiz in the shell, since I'm working blind? Is there something else I can try?

It might be that new kernel mode conflicting with my intel card?
I have one of those intel cards that suffered performance decreases in 9.04, and I had the driver downgraded.

---

### Post by geoffm on 2009-10-31
Ok, I removed compiz using the shell, and now it's fine. I guess compiz doesn't work with my graphic card for now. I'll just do without compiz.

---

### Post by dlight on 2009-11-01
I had the same problem with an Intel 945GM chip...

I'd really love to know if anyone has a fix for this issue...

---

### Post by geoffm on 2009-11-01
I reinstalled from scratch. It's flawless: compiz, suspend, and audio all work out of the box with the 2.6.31 kernel.

---

