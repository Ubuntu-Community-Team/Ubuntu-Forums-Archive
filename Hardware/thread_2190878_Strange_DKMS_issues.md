---
title: "Strange DKMS issues"
date: 2013-11-29
forum: Hardware
---

### Post by alexpavel97 on 2013-11-29
I recently found an updated driver for my RTL8812AU wireless chipset that works in kernels >= 3.10 (I'm on 3.12.1). I want to set up DKMS, but I have some weird issues. No matter how I write the dkms.conf "MAKE[0]= ... " section, it doesn't compile and gives the error ```
make: *** No rule to make target `all'.  Stop.
``` However, it I enter in something like ```
pwd && make
``` or ```
ls && make
``` it work perfectly. I looked at the make.log, and with the working commands, it seems to run the make command ```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.12.1-031201-generic/build M=/var/lib/dkms/8812au/4.22/build  modules
``` If I put that in the "MAKE[0]" section, once again I get the target error. Does anyone know what's happening and how I can make it work right? I partly want to know because I want to compile with 9 threads because it's a pretty large module and I have an 8 threaded processor and I also am really confused at why it doesn't work as I think it should. Here's the link to the driver on git if you need it: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

---

### Post by BertHartm on 2014-07-06
Sorry to bring up an old thread, but I was hitting the same issue.

Try the rule
```
MAKE="'make' KVER=${kernelver} KSRC=/lib/modules/${kernelver}/build"
```
(borrowed from [https://aur.archlinux.org/packages/rtl8812au-git-dkms/](https://aur.archlinux.org/packages/rtl8812au-git-dkms/))

That seemed to work for me.

---

