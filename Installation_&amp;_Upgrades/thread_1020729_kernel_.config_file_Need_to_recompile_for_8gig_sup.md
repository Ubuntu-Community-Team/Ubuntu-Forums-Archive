---
title: "kernel .config file? Need to recompile for 8gig support"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by g29115 on 2008-12-24
Can anyone explain to me where the .config file for the kernel source is hiding on a new 8.10 desktop install? I had to install the kernel source, but the .config used by the system or the Ubuntu team should be around my system somewhere...

If it is not that is very unhelpful and should be considered a bug. I need to recompile my kernel for large ram support, and would really rather not have to guess at all the options that were set for the system/hardware when it was installed.

Thanks.

---

### Post by oldos2er on 2008-12-24
Kernel config* files should be in /boot. The server kernel has PAE enabled, if you want to try that.

---

