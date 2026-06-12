---
title: "Linux 2.6.29 kernel crash K8+ powernow Ubuntu 9.04"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by wsuetholz on 2009-06-08
Hello,
  I had a hard time installing and upgrading 9.04 over the weekend.  I could not manage to get the installation CD's to run.  They would crash while trying to load the kernel.  So I couldn't even run the check CD function.  So, I tried installing 8.10 and upgrading.  Same thing happened.  As soon as the upgrade was finished and it tried to boot the new kernel it had a kernel panic.

  Eventually I noticed (a bit slow here) that the kernel panic was referencing the AMD K8 powernow code which in the past I've never got working.  I've always disabled the powernowd init script because it would just hang..  So, I started messing with the power settings in BIOS, and eventually got it to stop crashing..  The powernowd still hangs though.  I can probably reproduce/debug this problem if somebody wishes.  I can compile kernels, but not debug them presently.

System Information from memory:
  ECS EliteGroup KN1 Lite NVidia nForce4 Ultra based system board not sure about the BIOS release level.
  Athlon 64 3200+ processor (don't think it's an X2)

Thanks for any help

---

