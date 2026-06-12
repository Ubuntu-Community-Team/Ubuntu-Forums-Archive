---
title: "[SOLVED] How to temporarily disable powernowd"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Sasa Vilic on 2007-10-19
Is it possible:

- to temporarily disable powernowd without uninstalling the package oder restarting computer?
OR
-to temporarily set constant cpu frequency?

Thank you.

---

### Post by Sasa Vilic on 2007-10-20
After reading readme in source code package, i have found solution:

PAUSING:
--------

PAUSING was a feature added in v0.85, and removed in v0.90.  You can achieve
the same behavior by killing the daemon and restarting it, and I felt it 
wasn't worth the extra complexity and possible security concerns to keep 
this extra interface.

So, i have to only disable service.

---

