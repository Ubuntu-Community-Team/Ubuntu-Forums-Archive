---
title: "Trouble Building Kernel"
date: 2008-09-18
forum: General Help
---

### Post by NuNn DaDdY on 2008-09-18
When I try to build my kernel I receive the following error:

corey@NuNn-UbUnTu:/usr/src/linux-2.6.26.5$ sudo make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  CALL    scripts/checksyscalls.sh
  CHK     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  VDSOSYM arch/x86/vdso/vdso32-int80-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-sysenter-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syms.lds
  LD      arch/x86/vdso/built-in.o
  CC      kernel/module.o
  CC      kernel/kexec.o
  LD      kernel/built-in.o
  LD      vmlinux.o
  MODPOST vmlinux.o
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
<built-in>:0: fatal error: when writing output to /tmp/ccf3ah1u.s: No space left on device
compilation terminated.
make: *** [.tmp_kallsyms1.o] Error 1

---

### Post by manadi on 2008-09-19
Can you check the amount of free disk space you are having??

how much RAM do u have?

---

