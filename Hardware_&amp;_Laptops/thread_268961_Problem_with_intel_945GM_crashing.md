---
title: "Problem with intel 945GM crashing"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by jman2807 on 2006-10-01
I am running ubuntu 6.06 dapper drake on an intel 945GM and whenever I try to run some OpenGL applications it just crashes. On glxgears i get the following error:

libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted


If it makes a difference I do have compiz/aiglx installed however I get this error running gnome/metacity as well. Thanks in advance.

---

