---
title: "DKMS Problem"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2009-04-28
On a system with ATI HD3300 integrated motherboard graphics, I've been running linux with a custom 2.6.28.9 kernel, and the ATI Catalyst 9.4 proprietary drivers (module fglrx.ko). The ATI driver installs fine and everything works fine with this kernel.

Now I'm trying to upgrade to latest kernel 2.6.30-rc3, which has some non-graphics-related features I want. The 2.6.30-rc3 kernel compile and install works fine, and I'm able to start the system with the 2.6.30-rc3 kernel in recovery (non-graphics) mode. When I attempt to build and install the ATI fglrx.ko module for this new kernel, I get:

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.30-rc3 first.

and the build is unsuccessful. Apologies I'm not very familiar with 
DKMS - what do I need to do to build ATI fglrx.ko for my new kernel?

---

