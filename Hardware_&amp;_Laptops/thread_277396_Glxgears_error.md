---
title: "Glxgears error"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by jman2807 on 2006-10-14
Whenever I try to run any type of 3d game in ubuntu it crashes, so i decided to run glxgears to benchmark and It runs for about .2 seconds and then gives me this error:

libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted

I am running ubuntu DD 6.06, graphics chip is intel 945GM. Thanks in advance.

---

### Post by ahaslam on 2006-10-14
I got the same warning while testing an Edgy CD, but glxgears continued.

Have you tried the Intel driver?
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=955&DwnldID=9722&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=955&DwnldID=9722&strOSs=39&OSFullName=Linux*&lang=eng)


Tony.

---

