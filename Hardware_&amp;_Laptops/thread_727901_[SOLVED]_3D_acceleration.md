---
title: "[SOLVED] 3D acceleration"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by knowledge_is_power on 2008-03-18
Hey, I have a direct rendering problem i think
my fps for glxgears is terrible and i get the following error:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
I also get this error when Itry to run google earth.
I am and can, however, use compiz with 3D cube and the 3D screensavers just fine.
please help.

```
~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

Also:
CPU: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
GPU: ATI Radeon Xpress Series 128mb
and im using restricted drivers.

---

### Post by knowledge_is_power on 2008-03-18
no help?
should I uninstall XGL and install AIGLX instead?
get newer fglrx drivers?
any feedback on AIGLX at least?:confused::confused:

---

### Post by knowledge_is_power on 2008-03-19
bump plz.  also check my post out here:
[http://ubuntuforums.org/showthread.php?t=727755]("http://ubuntuforums.org/showthread.php?t=727755")

---

### Post by knowledge_is_power on 2008-03-20
**** yea.. the new ati drivers + AIGLX is freakin sweet.
i recommend it, just make sure you uninstall the drivers before upgrading to 8.10

---

