---
title: "Direct3D / wine problem"
date: 2009-11-23
forum: Hardware
---

### Post by MrReaper on 2009-11-23
Hello :)  Sorry for double posting but I found this might be more appropriate place for my problem.

I'm trying to get Direct3D working in wine (Diablo II LoD to be specific).

My PC is Asus Eee 901 (Atom270, Intel 945GSE chipset).

I've been running eeebuntu base 3.0 until last week and everything went really well (no performance issues even with D3D active). Now I'm running Ubuntu 9.10 and:
1) performance dropped somehow, even using DD. Graphics seem to be the bottleneck here (I assume it's graphic driver problem, since eeebuntu worked flawlessly).
2) I'm not getting option to choose D3D in D2VidTest. Seems like graphic driver issue to me as well.

Here is some info (xorg.conf - I read it works in Karmic if manually created):

```
Section "Device"
    Identifier "Intel Corporation Mobile Integrated Graphics Controller"
    Driver "intel"
EndSection
``````
jonas@REAP:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
``````
jonas@REAP:~$ egrep "(GLX|DRI)" /var/log/Xorg.0.log
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): direct rendering: DRI2 Enabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
```Everything looks fine to me but again, I've never dealt with graphic issues so far.

Can anyone help me please :) To be clear - missing D3D support is the issue, not the performance.

If you need any more information, just hit me with command line :) And if I'm somehow confused about the whole thing, feel free to point it out please (only by learning from our mistakes can we become perfect :) )

---

### Post by HeadHunter00 on 2009-11-23
use wine1.2 and I don't mean the version 1.2 I mean a software called "wine1.2". But before installing, add wine repositories from winehq.

---

### Post by MrReaper on 2009-11-24
> **HeadHunter00 said:**
> use wine1.2 and I don't mean the version 1.2 I mean a software called "wine1.2". But before installing, add wine repositories from winehq.

Sadly, I am using it already :/ Could this be trouble?

edit: Ok, it was :D I didn't consider this option since I was using wine1.2 on eeebuntu too but there I was switching to it from wine. Probably some config mismatch. Thanks Headhunter :)

---

