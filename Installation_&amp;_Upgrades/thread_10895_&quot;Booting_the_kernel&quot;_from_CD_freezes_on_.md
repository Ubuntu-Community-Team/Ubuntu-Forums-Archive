---
title: "&quot;Booting the kernel&quot; from CD freezes on Opteron."
date: 2005-01-12
forum: Installation &amp; Upgrades
---

### Post by aires on 2005-01-12
It was my first install of a Ubuntu - that I actually knew today only -, on an Opteron with 1Gb RAM and 1.3MHz.

I simply put the CD to boot, and the system freezes on "Booting the kernel". Attempts like "custom", "VERBOSE_LEVEL=5", "DEBUG_MODE=1" didn't return anything different (not even error messages). Any clues about what's happening?

Cheers,

Fernando Aires

---

### Post by aires on 2005-01-18
We found the problem, and solved it.

ACPI was turned on by default on BIOS. Properly turned off and boot has occurred normally.

Cheers,

---

