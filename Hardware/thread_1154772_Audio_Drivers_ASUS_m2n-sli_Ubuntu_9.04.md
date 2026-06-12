---
title: "Audio Drivers ASUS m2n-sli Ubuntu 9.04"
date: 2009-05-10
forum: Hardware
---

### Post by eddiemolko on 2009-05-10
Hi all, I recently installed Ubuntu on my PC.
The problem is that i cannot install the audio drivers.
My motherboard is an ASUS m2n-sli
When i try to install it, it sais:
ERROR: The NVIDIA kernel module was not created.

The log file contains:

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun May 10 05:43:09 2009

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-8)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.28-11-generic (buildd@palmer) (gcc
   version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59
   UTC 2009
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.28-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-11-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.28-11-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.28-11-gen
   eric/build SYSOUT=/lib/modules/2.6.28-11-generic/build'...
   make -C /lib/modules/2.6.28-11-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.28-11-generic \
   	KBUILD_EXTMOD="/tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main"
   -f /usr/src/linux-headers-2.6.28-11-generic/Makefile \
   	modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_ve
   rsions ; rm -f /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.
   tmp_versions/*
   make -f /usr/src/linux-headers-2.6.28-11-generic/scripts/Makefile.build obj=
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.nv
   alinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D_
   _KERNEL__ -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linu
   x-headers-2.6.28-11-generic/include -I/usr/src/linux-headers-2.6.28-11-gener
   ic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/us
   r/src/linux-headers-2.6.28-11-generic/ubuntu/include  -I/tmp/selfgz6080/NFOR
   CE-Linux-x86-1.0-0311-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -W
   no-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-decl
   aration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-st
   ack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestandin
   g -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx 
   -mno-sse2 -mno-3dnow -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/inc
   lude/asm/mach-default -Iarch/x86/include/asm/mach-default -fno-stack-protect
   or -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fwrapv  -I/tmp/selfgz6080/NFORCE-Linux-x86-1.0-0
   311-pkg1/nvsound/main 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error
   -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)"  -c -o /tmp
   /selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_nvalinux.o /tmp
   /selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:19:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a funciÃ³n â&#128;&#152;set_bitâ&#128;&#153;:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; en la aritmÃ©tica
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a funciÃ³n â&#128;&#152;clear_bitâ&#128;&#153;:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; en la aritmÃ©tica
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:19:
   include/linux/prefetch.h: En la funciÃ³n â&#128;&#152;prefetch_rangeâ&#128;&#153;:
   include/linux/prefetch.h:57: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:29:
   include/linux/scatterlist.h: En la funciÃ³n â&#128;&#152;sg_virtâ&#128;&#153;:
   include/linux/scatterlist.h:199: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *
   â&#128;&#153; en la aritmÃ©tica
   In file included from include/linux/smp_lock.h:5,
                    from include/linux/hardirq.h:5,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:30:
   include/linux/sched.h: En la funciÃ³n â&#128;&#152;object_is_on_stackâ&#128;&#153;:
   include/linux/sched.h:2025: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   In file included from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:37:
   include/linux/highmem.h: En la funciÃ³n â&#128;&#152;zero_user_segmentsâ&#128;&#153;:
   include/linux/highmem.h:136: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:136: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:136: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:136: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:139: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:139: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:139: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   include/linux/highmem.h:139: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; 
   en la aritmÃ©tica
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/i387.h:15,
                    from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:47:
   include/linux/regset.h: En la funciÃ³n â&#128;&#152;user_regset_copyoutâ&#128;&#153;:
   include/linux/regset.h:230: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:233: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:237: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h: En la funciÃ³n â&#128;&#152;user_regset_copyinâ&#128;&#153;:
   include/linux/regset.h:255: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:258: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:262: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h: En la funciÃ³n â&#128;&#152;user_regset_copyout_zeroâ&#128;&#153;:
   include/linux/regset.h:287: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:291: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h: En la funciÃ³n â&#128;&#152;user_regset_copyin_ignoreâ&#128;&#153;:
   include/linux/regset.h:312: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   include/linux/regset.h:314: aviso: se usÃ³ un puntero de tipo â&#128;&#152;void *â&#128;&#153; e
   n la aritmÃ©tica
   In file included from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:49:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.h: En e
   l nivel principal:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.h:46: e
   rror: tipos en conflicto para â&#128;&#152;uintptr_tâ&#128;&#153;
   include/linux/types.h:40: error: la declaraciÃ³n previa de â&#128;&#152;uintptr_tâ&#128;&#153; e
   staba aquÃ*
   In file included from /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:69:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvavm.h: En la f
   unciÃ³n â&#128;&#152;nv_flush_cachesâ&#128;&#153;:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvavm.h:215: err
   or: declaraciÃ³n implÃ*cita de la funciÃ³n â&#128;&#152;global_flush_tlbâ&#128;&#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvavm.h: En la f
   unciÃ³n â&#128;&#152;NV_SET_PAGE_ATTRIB_UNCACHEDâ&#128;&#153;:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvavm.h:234: err
   or: declaraciÃ³n implÃ*cita de la funciÃ³n â&#128;&#152;change_page_attrâ&#128;&#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c: En l
   a funciÃ³n â&#128;&#152;AosFpuSaveâ&#128;&#153;:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:181: 
   error: â&#128;&#152;struct task_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;thread_infoâ&#128;
   &#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:185: 
   error: â&#128;&#152;struct thread_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;i387â&#128;&#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:189: 
   error: â&#128;&#152;struct thread_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;i387â&#128;&#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:191: 
   error: â&#128;&#152;struct task_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;thread_infoâ&#128;
   &#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:214: 
   error: â&#128;&#152;struct task_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;thread_infoâ&#128;
   &#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:183: 
   error: l-valor invÃ¡lido en la salida asm 0
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:187: 
   error: l-valor invÃ¡lido en la salida asm 0
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c: En l
   a funciÃ³n â&#128;&#152;AosFpuRestoreâ&#128;&#153;:
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:234: 
   error: â&#128;&#152;struct task_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;thread_infoâ&#128;
   &#153;
   /tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:235: 
   error: â&#128;&#152;struct task_structâ&#128;&#153; no tiene un miembro llamado â&#128;&#152;thread_infoâ&#128;
   &#153;
   make[4]: *** [/tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nv
   alinux.o] Error 1
   make[3]: *** [_module_/tmp/selfgz6080/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.










Excuse me if my english is not so good, I'm from Argentina.

---

### Post by nascimentorodrigoe on 2009-06-06
I have the same problem here... Did you found the solution?
[EMAIL="nascimentorodrigoe@hotmail.com"]nascimentorodrigoe@hotmail.com[/EMAIL]

---

