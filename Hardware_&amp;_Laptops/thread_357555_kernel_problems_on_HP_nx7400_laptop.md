---
title: "kernel problems on HP nx7400 laptop"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by john_brown_jr on 2007-02-09
Hi Ubuntu folks,

Ubuntu does not show battery state on my HP nx7400, also Broadcom wireless card is not supported and suspend2ram does not work (laptop never recovers from suspend). I was able to get all of these things working on openSUSE after a lot of fiddling. I tried to do the same with Ubuntu, but without results so far.

So, I would like to migrate to 2.6.20 kernel. As I understand, suspend2ram should work starting from 2.6.19-rc5 kernels, and I also have patches for the battery state problem. I followed instructions from [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and successfully added 2 paches from [http://bugzilla.kernel.org/show_bug.cgi?id=7689](http://bugzilla.kernel.org/show_bug.cgi?id=7689). 

I compiled and installed the kernel, but now the new kernel does not boot - it crashes on boot with this:
PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
PCI: Not using mmconfig

I saw that some others had similar problems with 2.6.20x kernels on Ubuntu, but I never found a solution.

I would really, really appreciate any ideas or comments on my situation.

Best wishes,
John

---

### Post by john_brown_jr on 2007-02-13
UPDATE: I had these problems because I did not enable SATA support in kernel. That was actually quite tricky because I did not know which kernel modules to enable, but I manged to figure that out eventually.

---

### Post by capdog on 2007-02-22
Hi John Brown

What modules did you need? I'm trying to do a kernel compile and my SATA is also failing, I've got a 7300 HP which may be similar.

p.s. Which thread did you follow to recompile kernel? Thx!

Cheers
capdog

---

### Post by john_brown_jr on 2007-03-01
See this link: [http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95](http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95)

Hope it helps.

Cheers,
-/

---

