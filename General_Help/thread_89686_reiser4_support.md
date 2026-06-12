---
title: "reiser4 support"
date: 2005-11-13
forum: General Help
---

### Post by mykey on 2005-11-13
All right - going through the posts about reiser4 support in this forum I am aware that it is most likely to be not introduced - nevertheless I would like to be able to mount my reiser4 partitions - so - could anybody give me a hint where to look for kernel-patches/kernel-alternatives for reiser4 support? Hints are appreciated.

---

### Post by hachre on 2005-11-13
hi there,

the namesys reiser4 patches are here:
[ftp://ftp.namesys.com/pub/reiser4-for-2.6](ftp://ftp.namesys.com/pub/reiser4-for-2.6)

I think you have to kiss your ubuntu kernel goodbye though.
Get a full kernel from kernel.org which is included on that list...

Then patch it with a reiser4 patch from above and put reiser4 support in.

Maybe you can use ubuntus kernel config to compile your kernel...

I have no clue how to do this the ubuntu way. I'm using my own kernel with all drivers for my specific hardware compiled into it - no modules. 

I've read alot about reiser4. Some recent changes made it unstable and slower. They are working on that - i'm not sure about the current status.

If its unstable for you, try using kernel 2.6.13 or 2.6.12 instead of 2.6.14.

Good luck!

---

### Post by mykey on 2005-11-19
thanks for the link ;)

---

### Post by RAOF on 2005-11-19
And if you want to know how to build kernels the Ubuntu way, check out the [wiki page]("https://wiki.ubuntu.com/KernelHowto").

---

