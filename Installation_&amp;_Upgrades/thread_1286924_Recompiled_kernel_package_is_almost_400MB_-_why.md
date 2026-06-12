---
title: "Recompiled kernel package is almost 400MB - why"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by lotus49 on 2009-10-09
I have recompiled my kernel for my Acer Aspire One (annoyingly to change a single parameter - CONFIG_MMC_UNSAFE_RESUME) according to the instructions on the master kernel thread.  The compilation went fine but resulted in an enormous kernel package of almost 400MB.

I have previously recompiled using kernelcheck (which unfortunately currently has a fatal bug and is unusable) and the kernel package was <40MB as I would expect.

Does anyone have any idea why the recompiled kernel package is so huge?  Since this is a netbook with an 8GB SSD, I can ill afford a directory in /lib/modules that is almost 900MB, which is what resulted from installing the kernel package I had created.

---

### Post by lotus49 on 2009-10-09
Sorry, it appears I am guilty of inadequate searching before posting.

For some reason, make oldconfig appears to have set the kernel debugging flag resulting in an absurdly large kernel package.

I am currently recompiling but on my Aspire One, this is an overnight job so I shan't know for sure that this is the cause but I am fairly sure that it is.  If not, I shall report back.

---

