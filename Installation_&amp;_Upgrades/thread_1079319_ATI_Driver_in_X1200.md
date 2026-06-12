---
title: "ATI Driver in X1200"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by adri_ht_ on 2009-02-24
Hello guys,

I just recently update my kernel to 2.6.28.1 and I can't get the ATI wizard to compile and install the driver properly. Below is a log:

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.28.1/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-source-2.6.28.1'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;KCL_MEM_VM_GetRegionPhysAddrStr&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3221: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3222: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3223: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3225: warning: return makes pointer from integer without a cast
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_debug.o
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c: In function &#8216;KCL_DEBUG_Print&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c:89: warning: format not a string literal and no format arguments
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c: In function &#8216;__ke_printk&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/kcl_debug.c:146: warning: format not a string literal and no format arguments
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_ioctl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_io.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_pci.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_str.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_wait.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.28.1'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.
```

I tried the most recent drivers from ati.amd/com/support (Catalyst 8.12,9.1,9.2) and they all failed simirarly. ATI used to work flawlessly when I had an older kernel and Catalyst 8.2. Thanks

---

### Post by Mark Phelps on 2009-02-24
Could be a problem with the new kernel, but I have installed Catalyst 9.1 and replaced that with 9.2, in 8.10 without any problems.

---

