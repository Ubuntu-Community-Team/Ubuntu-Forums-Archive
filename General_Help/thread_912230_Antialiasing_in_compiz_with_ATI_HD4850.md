---
title: "Antialiasing in compiz with ATI HD4850"
date: 2008-09-06
forum: General Help
---

### Post by diobrando on 2008-09-06
So I just got a Radeon HD 4850 and it's now working with compiz and the latest (8.8) catalyst driver, but I can't seem to get antialiasing working. Setting the catalyst control center to override application settings and enable antialiasing has no effect. I had antialiasing working with my old geforce card but how would I go about it with an ATI card? Any suggestions?

---

### Post by diobrando on 2008-09-08
anyone?

---

### Post by bluezebra76 on 2008-09-14
I am also having this problem. I have an ATI 4850 with propriety drivers on fglrx. I set my antialiaing to max on the Catalyst Control Center and restarted the xserver. But then I realized this may be because some of the effects are 2d on a 3d surface and not actual edges (3d edges). For instance edges of window decoration are still 2d but when angled on the 3d it gets jagged. Like in windows switcher the angled 2d mockups of the window are still just that. So what we need is a way to tell it how to blur those angled 2d lines? I might be wrong here since this doesn't seem to happen when you do the cube but does happen when you do windows switcher. Any follow up thoughts?

---

### Post by diobrando on 2008-09-14
While I can't claim to be totally familiar with how antialiasing works with compiz, I think for some reason the catalyst control center isn't applying the settings, or not applying them globally, as when I had an nvidia card, I could change the antialiasing setting in the nvidia-settings application, then restart compiz, and everything appeared much smoother, including the cube.

---

