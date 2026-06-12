---
title: "R8186 driver make modules error"
date: 2008-06-28
forum: Hardware
---

### Post by Rafalukc on 2008-06-28
I'm trying to install the realtek r8168 driver however when i try to use the "make modules" command I get this error message:

make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[2]: *** No rule to make target `/src/Makefile'. Stop.
make[1]: *** [_module_/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

I'm new to linux I can't access the internet till I install this driver so any help would be much appreciated. I'm using ubuntu 8.04 with the 2.6.24-16 kernel.

---

### Post by AlexBellisBrown on 2008-06-28
Im assuming youre using the ethernet connection? And you cant get wireless working? This is an existing problem, i have the same problem, i cant get it to work either, my advice is you search Launchpad and make your views heard there... this has been a problem for sometime. I purchased a USB wifi stick, thats how i solved my problem.

---

