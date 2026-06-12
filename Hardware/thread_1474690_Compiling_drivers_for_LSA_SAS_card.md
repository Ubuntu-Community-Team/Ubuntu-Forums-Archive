---
title: "Compiling drivers for LSA SAS card"
date: 2010-05-06
forum: Hardware
---

### Post by hoggy on 2010-05-06
I have an LSISAS1068E that I'm attempting to make see a SAS tape drive in Ubuntu 10.04, and I can't quite make it work.

I've downloaded the driver source ala 'mptlinux-4.22.00.00-src.tar.gz'.  After exploding it all into '/usr/src', I find I'm looking at something pretty foreign.

```
root@testbak:/usr/src/SLES10/message/fusion# ls
clean           load       mptctl.c    mptlan.h    mptspi.c         update
compile         lsi        mptctl.h    mptsas.c    pound
csmi            Makefile   mptdebug.h  mptsas.h    rejected_ioctls
Kconfig         mptbase.c  mptfc.c     mptscsih.c  scripts
linux_compat.h  mptbase.h  mptlan.c    mptscsih.h  uload

```

So I try...

```
root@testbak:/usr/src/SLES10/message/fusion# make menuconfig
make: *** No rule to make target `menuconfig'.  Stop.

```
```
root@testbak:/usr/src/SLES10/message/fusion# make clean
make: Nothing to be done for `clean'.

```

etc, etc, etc

Help?

---

