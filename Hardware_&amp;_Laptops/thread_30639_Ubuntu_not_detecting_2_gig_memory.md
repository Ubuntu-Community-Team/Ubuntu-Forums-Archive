---
title: "Ubuntu not detecting 2 gig memory"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by acantril on 2005-04-29
Anyone experienced an issue where ubuntu wouldnt detect all their memory ? i have 2 gigs of pc3200 in this machine, under windows its detected fine, bios sees it fine, but on bootup linux says

Memory: 902040k/917504k available (1436k kernel code, 14932k reserved, 754k data, 224k init, 0k highmem)


Any ideas ?

---

### Post by ebrowne on 2005-04-29
I beleive you have to turn on Highmem support in the kernel I beleive the -smp kernels have this by default.

---

### Post by ZiZe on 2005-04-30
you have to install a -686 kernel to use all your memory.
that fixed it for me.

---

