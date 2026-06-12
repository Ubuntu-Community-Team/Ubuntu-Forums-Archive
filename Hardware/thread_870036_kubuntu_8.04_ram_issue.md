---
title: "kubuntu 8.04 ram issue"
date: 2008-07-25
forum: Hardware
---

### Post by Lormen on 2008-07-25
hi, i built my kubuntu hardy install on a dual core intel with 3GB of RAM i recently installed another 3 GB which the bios can see but linux cant, is there something I need to do?

TIA

Peter

---

### Post by jimv on 2008-07-25
If you're using the x86 (32 bit) version of Ubuntu, then it won't see the entire 6 gigs.  A 32 bit OS can only address ~4 gigs of RAM.  You need the 64 bit version of Ubuntu (AMD64).

---

### Post by prshah on 2008-07-25
> **Lormen said:**
> 
intel with 3GB of RAM i recently installed another 3 GB which the bios can see but linux cant

You can:

1) Switch to using (K)Ubuntu 64-bit

or

2) Enable PAE extensions in your kernel (will require a kernel recompile). Physical Address Extensions allow a 32-bit operating system to access more than 3.2Gb RAM; this is a limitation to all 32-bit OS's, not just linux. Enabling PAE allows access to upto 64Gb (?) RAM.

---

### Post by zgornel on 2008-07-25
You can also install the 'server' version of the kernel via the package manager (it has PAE enabled by default).

---

