---
title: "Test 2.6.30 Kernel Set up question"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2009-05-27
I have a new drive all set-up for testing new kernels and pre-releases. 

I want to compile and setup 2.6.30-rc7 on that separate drive. I do not believe I can get an iso for it, so how would one go about getting it setup?

Thanks....

---

### Post by lemming465 on 2009-05-30
One fairly easy way is to install a secondary copy of whatever fairly recent version of Ubuntu you favor to a partition on the separate drive, and boot it.  In these sorts of situations I make sure to put the GRUB bootloader for the secondary install onto the actual root partition itself, and then add a chainloader clause to my main grub menu to go there instead.

Then follow the directions at [Kernel Mainline Builds]("http://https://wiki.ubuntu.com/KernelMainlineBuilds")

---

