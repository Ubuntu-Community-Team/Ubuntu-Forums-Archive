---
title: "Nvidia Compiz Dual Screen - Twinview issue"
date: 2008-09-15
forum: General Help
---

### Post by gus_393 on 2008-09-15
I saw a guy having the exact same problem as me, and far as I can tell from some pretty extensive searching, this is not addressed anywhere.

From what I`ve found so far,
It appears that one has to use twinview (not xinerama) to get this setup working properly. The problem is, with twinview enabled, I`m getting two "shells" if you will. That is, i can see the taskbar/drop downs on both displays when I only want to see them on one.

Does anyone know a setting to force twinview to work analogous to xinerama (where the desktop stuff only shows on one display).

The central issue is that when using xinerama, the composite extension does not appear to run properly (even if setup in xorg.conf). With twinview it runs, but with the redundant display (that appears to lag quite badly).

if I get something working I`ll post it.

And a related note, I find that with compiz enabled my right-click menus take a notable amount of time to appear. Is there a work around for this? In fact in general, the effects appear to lag for me.

---

