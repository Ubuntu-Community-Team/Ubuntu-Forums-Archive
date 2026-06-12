---
title: "Kernel update. How?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by hambos22 on 2009-07-02
I have ubuntu 9.04. I read that kernel 2.6.30 fixes the problem with intel driver. How can i update my kernel to 2.6.30? now i have 2.6.28.

---

### Post by lemming465 on 2009-07-04
It depends on whose kernel you want.  For a newer ubuntu kernel you'd want to enable the karmic koala main repository and probably pin the non-kernel packages.  It's easier, but possibly buggier, to use the [main line kernel builds]("https://wiki.ubuntu.com/KernelMainlineBuilds").  I used a mainline build recently when I ran into a realtek ethernet driver bug in 2.6.28 that was fixed in 2.6.30, for example.

---

