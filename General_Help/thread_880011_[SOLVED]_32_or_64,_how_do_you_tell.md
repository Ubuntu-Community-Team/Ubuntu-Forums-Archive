---
title: "[SOLVED] 32 or 64, how do you tell?"
date: 2008-08-04
forum: General Help
---

### Post by d_in_Conduct on 2008-08-04
When you sit down at an unfamiliar system, or just plain forgot, how do you tell whether it is running a 32 or 64-bit system?

---

### Post by tgrimley on 2008-08-04
You can do uname -a and it'll tell you the kernel.

---

### Post by y@w on 2008-08-04
```
uname -m
```

That will tell you the architecture the machine is on.

i686 for 32-bit and x86_64 for 64-bit systems.

```
uname -a
```

That will show you all the kernel info for you system.

---

### Post by scragar on 2008-08-04
Odds are unless it's a server it's a 32 bit system.

Few ways to check for sure though if that's not good enough for you:
firstly on linux```
uname -m
``` or the hardware monitor in windows should let you know.

---

### Post by d_in_Conduct on 2008-08-04
Thanks to all.  That was the information I needed. :)

---

