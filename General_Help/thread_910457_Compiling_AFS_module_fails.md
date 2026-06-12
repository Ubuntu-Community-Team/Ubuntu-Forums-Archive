---
title: "Compiling AFS module fails"
date: 2008-09-04
forum: General Help
---

### Post by Knorr on 2008-09-04
Hi.

I'm trying to get the openafs client running on my laptop, and for that I apparently need to compile the openafs-module. This however seems like a quite error prone task.

I'm running Intrepid 64bit with kernel 2.6.27-2-generic with headers and source installed.

When I try to compile the module I get an error. Here follows the last part of the build output.

```

Building in directory: MODLOAD-2.6.27-2-generic-MP
make[4]: Entering directory `/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP'
Makefile.common:50: warning: overriding commands for target `.c.o'
/usr/src/modules/openafs/src/config/Makefile.config:135: warning: ignoring old commands for target `.c.o'
Makefile.afs:166: target `openafs.ko' given more than once in the same rule.
Makefile.afs:171: warning: overriding commands for target `openafs.ko'
Makefile.afs:167: warning: ignoring old commands for target `openafs.ko'
Makefile.afs:203: warning: overriding commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
Makefile.afs:200: warning: ignoring old commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
make[4]: Circular openafs.ko <- openafs.ko dependency dropped.
make[4]: Circular openafs.ko <- openafs.ko dependency dropped.
env EXTRA_CFLAGS="" /usr/src/modules/openafs/src/libafs/make_kbuild_makefile.pl MODLOAD-2.6.27-2-generic-MP openafs.ko /usr/src/modules/openafs/src/config/Makefile.config Makefile.afs Makefile.common
env EXTRA_CFLAGS="" make -C /usr/src/linux-headers-2.6.27-2-generic M=/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP modules
make[5]: Entering directory `/usr/src/linux-headers-2.6.27-2-generic'
  CC [M]  /usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP/afs_atomlist.o
gcc: -pg and -fomit-frame-pointer are incompatible
make[6]: *** [/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP/afs_atomlist.o] Error 1
make[5]: *** [_module_/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP] Error 2
make[5]: Leaving directory `/usr/src/linux-headers-2.6.27-2-generic'
make[4]: *** [openafs.ko] Error 2
make[4]: Leaving directory `/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.27-2-generic-MP'
make[3]: *** [linux_compdirs] Error 2
make[3]: Leaving directory `/usr/src/modules/openafs/src/libafs'
make[2]: *** [libafs] Error 2
make[2]: Leaving directory `/usr/src/modules/openafs'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/openafs'
make: *** [all] Error 2

```

I can't really get anything out of this. Does anyone know what could be wrong?

---

### Post by Washer on 2008-09-06
you're using the right gcc?

---

### Post by Knorr on 2008-09-06
> **Washer said:**
> you're using the right gcc?

I've tried compiling with version 4.3, 4.2 and 3.4.
A friend of mine compiled his successfully with 4.2, haven't seen any requirements as to which version you should use.

---

### Post by cbhl on 2008-09-07
As far as I can see, OpenAFS does not compile with 2.6.27 (the kernel in Intrepid), at all.

Your particular error appears to be an issue with optimization or some such... are you compiling from OpenAFS sources, or using module-assistant?

---

### Post by Knorr on 2008-09-07
> **cbhl said:**
> As far as I can see, OpenAFS does not compile with 2.6.27 (the kernel in Intrepid), at all.

Your particular error appears to be an issue with optimization or some such... are you compiling from OpenAFS sources, or using module-assistant?

I've tried compiling the source from the openafs-module-source package directly and via module-assistant. I've also tried compiling the newest version from openafs.org

I'll try compiling under 2.6.26

---

### Post by Knorr on 2008-09-07
> **Knorr said:**
> I've tried compiling the source from the openafs-module-source package directly and via module-assistant. I've also tried compiling the newest version from openafs.org

I'll try compiling under 2.6.26

Compiled successfully under 2.6.26. Guess I'll open a bug report on launchpad.

---

