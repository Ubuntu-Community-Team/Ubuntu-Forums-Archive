---
title: "make gconfig behaves strange"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by landersohn on 2009-11-09
I have been trying to compile the 2.6.31 kernel from the kernel.org repositories.
With the default configuration file everything builds and runs just fine. I tried to optimize the configuration a bit and disabled all Network Address Translation related items (i.e. I said "N" to the topmost item in gConfig.
Turns out when I try to boot this kernel my graphics support is gone: I get the message that I  am oin low resolution graphics mode.
Enabling NAT and compiling and everything is fine. It may seem that gConfig sets a few flags that it should not?

Did anybody come across a similar behavior?

---

