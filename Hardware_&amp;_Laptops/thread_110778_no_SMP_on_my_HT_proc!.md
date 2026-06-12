---
title: "no SMP on my HT proc!?"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by zambizzi on 2005-12-31
I'm a former Gentoo user as of today...can't see myself going back after all the trouble I've had lately (poor Q/A, instability, etc.)...AND especially after using Ubuntu - fantastic distro guys!!

Anyhow...I'm used to doing everything manually...including compiling the kernel.  I noticed that SMP was not detected on this machine and it's only showing a single proc...which would show as two since it's a Intel HT 3.0GHz proc. if SMP had been enabled in the kernel.

How dangerous would it be for me to just compile a new kernel myself in Ubuntu?  Any gotchas I should know about first?

In Gentoo I would compile a new one in /usr/src/linux (symlink), copy the kernel, System.map, and .config to /boot and then point grub to the new kernel.  Anything I should know about before trying?

Thanks!

**EDIT**

I noticed that there's an 'smp' version of my kernel in apt...should I just install that and remove the old non-smp kernel?  Anything to worry about there?

---

### Post by x1alfa on 2006-01-01
Hi,

I have the same issue, i did the download and the installation for the kernel with the (SMP) support and my ubuntu box is just working fine with an amazing speed and stability.

Just go to (add application --> advanced --> and search for (SMP) --> then select the linux image SMP) --> download and install. that's it you have kernel with support for multi prossesor.

I have the system monitor with cpu1 and cpu2 now.

Regards

---

### Post by zambizzi on 2006-01-01
Yeah, I actually went for it and installed it after posting.  At first I didn't realize I needed the restricted modules as well (why wasn't that a dependency since I had nvidia-glx installed?)

Anyhow, once I straightened that out I was good to go.  I'm VERY impressed at how simple and stable ubuntu is...I thought I'd be a Gentooist for life.

---

