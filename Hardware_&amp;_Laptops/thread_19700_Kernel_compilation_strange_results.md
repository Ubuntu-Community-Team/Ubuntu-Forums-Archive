---
title: "Kernel compilation strange results"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by milou on 2005-03-13
Hello. I wanted to compile a kernel myself. But I get strange results. I want to compile kernel 2.6.10-4-386 but if I compile and install myself I get wrong hald behaviour:

"your kernel does not support hald capabilities " or something like that. It does not appear with the ubuntu deb !!! Though I compiled and prepared my custom deb. package with the same ".config"  as the  one of the stock kernel. What does that mean ????

Eric

---

### Post by az on 2005-03-13
Where did you get the source?  If you install the linux-source package, you get all the debian/ubuntu patches along with the source.  If you get the source from kernel.org, you are missing stuff.  One you install the linux-source package, the patches are listed in /usr/share/doc/linux-source....

---

### Post by milou on 2005-03-14
I compiled from ubuntu debian source : linux-source-2.6.10 package, and config from linux-image-2.6.10 package .... maybe there is a kernel patch package for 2.6.10 ?

---

