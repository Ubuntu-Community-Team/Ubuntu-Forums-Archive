---
title: "flash player problem"
date: 2008-10-18
forum: General Help
---

### Post by yanom on 2008-10-18
I installed every flash plugin i can find on Synaptic, enabled all of the software sources, and i still cant get any flash things to work in firefox. why?

---

### Post by Yellow Pasque on 2008-10-18
Installing multiple flash plugins might be a problem. Exactly what packages did you install, flashplugin-nonfree, gnash, swfdec? Most users will probably want to install flashplugin-nonfree (and libflashsupport for sound with PulseAudio).

Are you using a 64-bit install (look at uname -m if unsure)? If so, see the sticky in the x86-64 subforum.

Does a flash plugin show when you enter about:plugins in the URL bar?

---

