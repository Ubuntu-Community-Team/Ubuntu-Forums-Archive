---
title: "ati errors"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by atad6 on 2005-09-18
hi,
i'm trying to install the new ati drivers, i just installed the build-essentials, the linux header files and source, now when i try to install the drivers i get this in the install log:

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
make -C /lib/modules/2.6.12-8-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/agp3.o] Error 127
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
``` 

I'm guessing it's because I'm missing a package I need. I'm fairly new to linux so any help would be greatly appreciated.

Thanks!

---

### Post by krak on 2005-09-18
run Synpatic and search for GCC and install gcc-3.4 should do if not try my ati howto did work for me and others
[http://www.ubuntuforums.org/showthread.php?t=66445](http://www.ubuntuforums.org/showthread.php?t=66445)

---

