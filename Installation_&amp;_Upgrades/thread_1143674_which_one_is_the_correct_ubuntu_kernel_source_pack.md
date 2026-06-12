---
title: "which one is the correct ubuntu kernel source package?"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by catarano on 2009-04-30
is it linux-source or linux-ports?

when i try to recompile the kernel I use the config file that comes in the boot directory which matches the ubuntu kernel installed by default

however, while recompiling I can see that several parameters in the config file were not set

is that the right config to use?

the only parameters that I change relative to the default kernel is the timer speed (set to 1000 Hz) and I deselect the v4l kernel modules which i subsequently recompile by source

However the machine boots quite differently (slower) and gives me some problem when I try to shut it down (only logs out)

with the default kernel everything is fine

so i guess there is something missing

Thank you

---

