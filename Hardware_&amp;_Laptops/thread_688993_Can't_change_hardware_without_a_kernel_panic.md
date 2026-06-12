---
title: "Can't change hardware without a kernel panic?"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Corgana on 2008-02-05
So I'm moving my old media server PC to a smaller case, one that doesn't have room for a CD-ROM drive, but no matter how I arrange the hardware, if it is even SLIGHTLY different (secondary master and slave HD's switched, or even just changing one to "cable select" instead of it's current setting, for example) I'll get "kernel panic -- not synching: attempting to kill init" and it won't boot whatsoever.

Any ideas as to what may be causing this? it's driving me crazy having my hardware half inside the new case.

Thanks in advance!

---

### Post by chrisdeckard on 2008-02-06
What are the messages previous to that?  It's probably not finding the root (/) filesystem to mount, and so yes, the kernel will panic when it cannot mount /.  Look for more info in the error messages/output on the screen.

-Chris

---

