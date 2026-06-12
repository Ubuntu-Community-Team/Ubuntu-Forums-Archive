---
title: "make-kpkg clean Xen?"
date: 2008-10-21
forum: General Help
---

### Post by undrex on 2008-10-21
Keep getting this error when trying make-kpkg clean! Anyone got a solution for this? The reason its not finding the Xen directory is because its not there ofcource :)

root@X:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
make[1]: Entering directory `/usr/src/linux-2.6.27.2'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=xen distclean
make[2]: Entering directory `/usr/src/linux-2.6.27.2'
Makefile:518: /usr/src/linux-2.6.27.2/arch/xen/Makefile: No such file or directory
make[2]: *** No rule to make target `/usr/src/linux-2.6.27.2/arch/xen/Makefile'.  Stop.
make[2]: Leaving directory `/usr/src/linux-2.6.27.2'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.2'
make: *** [CLN-common] Error 2

Best regards

---

### Post by ohboyotero on 2008-10-30
I'm also having the same problem. Any ideas as to what might be the best solution?

Thanks!

---

### Post by ohboyotero on 2008-10-30
Alright I think I fixed. My particular compilation config was calling for Xen support. If you reconfigure (e.g. menuconfig), and then make sure that no Xen-related options are selected, then retry the make-kpkg clean, it should work.

Note that they may be in deeper sub-menus. Mine, for instance, was inside of Processor Type and Features >> Paravirtualized Guest Support >> Xen ...

Good luck :)

---

### Post by Afi on 2008-11-06
Thank you for this. :) It's a bit hard sometimes when you don't know what your doing.

---

### Post by MianoSM on 2008-11-28
What would you do if you wanted Xen support though? 

This is a good work around, but it doesn't seem like it would work in the case that a user was attempting a custom kernel for a xen system/host?

---

