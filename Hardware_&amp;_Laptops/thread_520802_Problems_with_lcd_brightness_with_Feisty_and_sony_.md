---
title: "Problems with lcd brightness with Feisty and sony vaio pcg-k315s"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by Erik Bekkering on 2007-08-08
Hi everybody,
I've installed Feisty on my Sony vaio PCG-K315S. Everything works fine, but the power management won't set the lcd brightness.
I had this problem also with Breezy, and fixed it by changing /bin/sh in /bin/bash in the set-lcd-brightness/get-lcd-brightness files. This won't work with Feisty. Does anyone know a solution for this problem?
My vaio uses an ati radeon chipset

---

### Post by Erik Bekkering on 2007-08-13
> **Erik Bekkering said:**
> Hi everybody,
I've installed Feisty on my Sony vaio PCG-K315S. Everything works fine, but the power management won't set the lcd brightness.
I had this problem also with Breezy, and fixed it by changing /bin/sh in /bin/bash in the set-lcd-brightness/get-lcd-brightness files. This won't work with Feisty. Does anyone know a solution for this problem?
My vaio uses an ati radeon chipset

I've found the solution myself:
There seems to bee 2 sets of ..lcd-set-brightness... scripts.
You have to change the #!/bin/sh into #!/bin/bash in hal-system-lcd-get-brightness-linux and hal-system-lcd-set-brightness-linux in the /usr/lib/hal/scripts/linux directory. It works great with my vaio.

---

