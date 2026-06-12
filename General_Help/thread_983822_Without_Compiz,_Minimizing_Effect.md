---
title: "Without Compiz, Minimizing Effect?"
date: 2008-11-16
forum: General Help
---

### Post by Roasted on 2008-11-16
Using Compiz, I have video tearing with DVDs and whatnot, so I decided to keep Compiz disabled. However, without Compiz when I minimize windows, I get a high speed gray outline of a box several times around a window that I minimize. It's not a big deal, but can I get rid of that? Can I set it so instead of the window I minimize getting smaller and traveling to the lower task bar that it just... POOF! vanishes? That way I wouldn't see the weird black box outlines around it as it trails down to the lower taskbar.

Not a big deal, just a general question as to whether or not I can still control window management without Compiz.

EDIT - I found a fix after searching for a while in the search function, imagine that?

Two step process here.

1 - Open gconf-editor (ALT + F2 and type gconf-editor)
  - Go to apps/metacity/general and check the box for "reduced resources"

This will take away the minimizing black box outlines, however, it will enable a wire-frame over the windows as you move them.

To get rid of the wire-frame...

2 - System - Preferences - Assistive Technologies
  - Check the box for enabling it.

Done.

However, even though this works, I'm still left wondering why. Why does the wire frame box appear? Why does enabling assitive technologies disable the wire frame box? Can anybody tell me? Is there anyway else to get rid of this black box thing when minimizing windows besides what I just posted above?

---

