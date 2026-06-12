---
title: "How to compile drivers...what am I missing?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by neilneil2000 on 2009-08-09
Hi all, 

I am trying to compile a driver for my r8101 network card.  I have done it before (many months ago)  but now can't get it to work for the life of me.

I have followed the readme instructions, and this is the outcome:

```

neil@Mediacentre:~/Compiled$ tar xvjf r8101-1.013.00.tar.bz2
r8101-1.013.00/
r8101-1.013.00/readme
r8101-1.013.00/Makefile
r8101-1.013.00/src/
r8101-1.013.00/src/r8101_n.c
r8101-1.013.00/src/Makefile_linux24x
r8101-1.013.00/src/rtl_eeprom.c
r8101-1.013.00/src/Makefile
r8101-1.013.00/src/rtl_eeprom.h
r8101-1.013.00/src/rtl_ethtool.h
r8101-1.013.00/src/r8101.h
neil@Mediacentre:~/Compiled$ cd r8101-1.013.00/
You have new mail in /var/mail/neil
neil@Mediacentre:~/Compiled/r8101-1.013.00$ ls
Makefile  readme  src
neil@Mediacentre:~/Compiled/r8101-1.013.00$ sudo make modules
make -C src/ modules
make[1]: Entering directory `/home/neil/Compiled/r8101-1.013.00/src'
make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/neil/Compiled/r8101-1.013.00/src'
make: *** [modules] Error 2

```

I assume the "scripts/Makefile.build:41: /src/Makefile: No such file or directory" is the problem.

What am I missing?  I have checked the following and they are all installed:

build-essential
linux-headers-2.6.28-11-server
linux-headers-lbm-2.6.28-11-server

I may be barking up the wrong tree, but I don't know what else to check.

Please help!

---

### Post by smallming on 2009-09-02
Hope you got your kernel version right. Try uname -r?

---

