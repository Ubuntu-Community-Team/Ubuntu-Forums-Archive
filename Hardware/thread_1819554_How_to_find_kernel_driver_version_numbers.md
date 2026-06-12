---
title: "How to find kernel driver version numbers ?"
date: 2011-08-06
forum: Hardware
---

### Post by declanmullen on 2011-08-06
Hi 

I would like to find out the version numbers of some device drivers that are included in a couple of kernels. Apart from installing the kernel sources and reading them, is there another way to find out the driver versions ?

In particular the hardware in question is a "Leadtek WinFast DTV2000DS" and the drivers modules for it are called tda18271 and af9013. 

The first kernel is the latest for ubuntu 10.10 x86 32bit:
```
$ uname -a
Linux pvr 2.6.35-30-generic-pae #56-Ubuntu SMP Mon Jul 11 21:51:12 UTC 2011 i686 GNU/Linux
```

The second kernel is the latest for ubuntu 11.04 x86 32bit:
```
$ uname -a
Linux pvr 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux

```

Thanks,
Declan

---

