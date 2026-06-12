---
title: "problem installing ubuntu 64 bit"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by jsvidyad on 2006-09-18
Hi!!!

  I have a dell inspiron E1505 with a Core 2 Duo processor T7400. When I put in the Live Cd to install ubuntu, I am getting this message:

Loading hardware Drivers...
[ 106.338747] Kernel Panic - not syncing : PCI-DMA :high address but no IOMMU
[ 106.339025]  



Then the computer just freezes. Iam trying to install 64 bit ubuntu

---

### Post by x64Jimbo on 2006-09-18
did you check your iso's md5sum before burning it, and did you burn at a low speed? You may have a corrupt CD there.

---

### Post by siersmak on 2006-10-03
Perhaps I'm too late, but I had the same problem.  I found that you can boot and install if you pass the 'iommu=soft' option to the kernel.

-Ken

---

