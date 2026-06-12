---
title: "[Solved] Kernel upgrade video problem - Ubuntu 8.04"
date: 2008-10-15
forum: General Help
---

### Post by Oldster on 2008-10-15
This mornings kernel upgrade left me with video in failsafe mode. I found the corresponding restricted modules package did not get installed. Apparently no Nvidia driver was available. The solution is to manually install:

linux-restricted-modules-2.6.24-21-386

I hope this helps someone else.

---

