---
title: "synaptic seg faults after 9.04 update"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Ceratog on 2009-04-21
Hello,

I am on a 64bit system running 8.10. A few moments ago I updates to 9.04 using the update manager. Now when I launch synaptic I am prompted for the sudo password and when I enter that, synaptic come up for a moment and then throws a seg fault.

kernel: [ 2981.248482] synaptic[5834]: segfault at 7f25726c92a8 ip 00007f2572cb6070 sp 00007fff7b159510 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f2572c7b000+bc000]

Any ideas?

Thanks in advance.

---

### Post by Ceratog on 2009-04-21
Fixed!

rename both 

/var/cache/apt/pkgcache.bin
/var/cache/apt/srcpkgcache.bin

to pkgcache.bin.old and srcpkgcache.bin.old

Works like a dream.

---

