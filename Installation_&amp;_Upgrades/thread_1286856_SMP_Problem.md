---
title: "SMP Problem"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by glj on 2009-10-09
About a year ago I upgraded a server to Edubuntu 8.04. Being new to the school, I didn't realize that the server was running slower than it had previously. Yesterday I discovered why. cpuinfo showed only one processor being used on the dual Xeon (2.8GHz) server. With 17 thin clients attached, "top" shows that the one processor is often at 100% utilization. The kernel is Linux 2.6.24-24-386. Is that not the right kernel? If that kernel should boot up using SMP, why isn't it? How can I get it to use SMP? If that kernel is not the right one to use on this dual Xeon server, which kernel should I install?

---

### Post by glj on 2009-10-09
Solved! Apparently, grub was by default selecting a kernel that does not support SMP. When I booted the server this time, I selected the generic version of the kernel and, voila, four processors appear in System Monitor! Yea!

---

