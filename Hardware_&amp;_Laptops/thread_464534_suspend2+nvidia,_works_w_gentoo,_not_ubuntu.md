---
title: "suspend2+nvidia, works w/ gentoo, not ubuntu"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by jawilson on 2007-06-04
I have a question about suspend2. I have used gentoo for several years, and using their suspend2 patches and the latest nvidia driver (9755, I think), suspend2 works PERFECTLY with both ram and hibernate (it is a 2.6.18 kernel, I think). Well, since this is linux, as soon as everything works perfectly, I need to break it :-), so I installed ubuntu on a separate partition. Since the stock ubuntu kernel does not support suspend2, I have tried to recompile the ubuntu kernel with suspend2 patches, and suspend2ram and hibernate do not work; they both freeze when resuming. So, I recompiled my gentoo kernel with an IDENTICAL .config, and booted it with ubuntu, and it still does not work. All of the loaded modules are the same, and all modules compiled into the kernel are the same (a diff between the gentoo and ubuntu .config files shows nothing). So, if my kernel and nvidia drivers are identical, my hibernate scripts are (mostly) identical, what else could be causing the hangup? Are there any services I should stop? Any other ideas?

---

