---
title: "Transparent task bars without drop shadow?"
date: 2008-11-27
forum: General Help
---

### Post by ac3raven on 2008-11-27
I like the look of completely opaque task bars that do not have drop shadow.  But I realized that the only way to keep it this way is to disable desktop effects.  Is there any way to enable compiz while keeping the task bar, shadow-free?

---

### Post by Arylon on 2008-11-27
Try this:
Open the CompizConfig Settings Manager. In the settings for Window Decoration, set Shadow windows to "any & !(class=Gnome-panel)". This way, the panels (task bars) will not have shadows, but all other windows will.

---

### Post by ac3raven on 2008-11-27
that did it, thanks a bunch!

---

