---
title: "kernel upgrades break modules"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by lee_connell on 2006-05-08
Just a general question, when a new kernel is installed i have to recompile modules that i have installed.

now how does it differ from when you compile modules yourself and modules that you install as a compiled package?

for instance, i installed ndiswrapper from source and i have to recompile when the kernel gets upgraded, now if i downloaded it from the repos i wouldn't have to do anything, what happens here?

Thanks!

---

### Post by louis_nichols on 2006-05-09
Such packages have their dependencies set on a certain version of the kernel. So if a certain module requires a certain kernel, the module will be updated in the repos aswell. I haven't checked how fast that is done, though. I only have the nvidia driver in such a situation, and never experienced an instance where I upgraded the kernel and the driver wasn't updated.

---

