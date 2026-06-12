---
title: "something missing from make"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2005-01-26
I've just installed a new version of ubuntu on a new desktop and am attempting to make a required version of the alsa driver.  For some reason it will not compile, suspect I am missing some critical part of make or automake or autoconf or something!  Can anyone tell me from the attached error what I'm missing so I can load it?

Thanks

Jim

jamaas@jamdesktop:~/downloads/alsa-driver-1.0.8 $ make
make[1]: Entering directory `/home/jamaas/downloads/alsa-driver-1.0.8/acore'
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #2 succeeded at 165 with fuzz 2.
Hunk #3 succeeded at 366 (offset -4 lines).
Hunk #4 succeeded at 381 (offset -6 lines).
Hunk #5 succeeded at 496 (offset -7 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1341 (offset 25 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 995 (offset 26 lines).
Hunk #2 succeeded at 1805 (offset 72 lines).
Hunk #3 succeeded at 1833 (offset 52 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 321 (offset 29 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
gcc -D__KERNEL__ -DMODULE=1 -I/home/jamaas/downloads/alsa-driver-1.0.8/include  -I/usr/src/linux/include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include   -DEXPORT_SYMTAB -c memalloc.c
In file included from memalloc.c:1:
memalloc.inc:1:26: linux/config.h: No such file or directory
memalloc.inc:2:27: linux/version.h: No such file or directory
memalloc.inc:4:40: missing binary operator before token "("
memalloc.inc:12:23: linux/pci.h: No such file or directory
In file included from memalloc.inc:14,
                 from memalloc.c:1:

---

### Post by imightbegiant on 2005-01-26
I'd try to sudo apt-get install build-essential first.  Just a guess.

---

