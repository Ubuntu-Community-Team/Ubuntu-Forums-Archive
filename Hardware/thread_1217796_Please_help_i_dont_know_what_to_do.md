---
title: "Please help i dont know what to do"
date: 2009-07-19
forum: Hardware
---

### Post by rorrometal on 2009-07-19
I tried to install nvidia driver but i have this problem.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jul 19 23:42:08 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce FX 5200 GPU installed in this system is supported
         through the NVIDIA 173.14.xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 185.18.14 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.14
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 185.18.14.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-11-gener
   ic/build SYSOUT=/lib/modules/2.6.28-11-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-11-generic/build SUBDIRS
   =/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.1
   4-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include -
   include include/linux/autoc
   onf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign
   -compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3d
   now -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-poin
   ter-sign -fwrapv -I/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -
   o /tmp/selfgz4436/NVIDIA-Linux-x86-
   185.18.14-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.
   14-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/includ
   e -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-p
   ointer-sign -fwrapv -I/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpa
   rentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_nv-vm
   .o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4436/NVIDIA-Linu
   x-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfo
   rmat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror 
   -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4436/NVIDIA-Linux-x86-185.
   18.14-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.
   14-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include 
   -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86
   /include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -
   Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-i
   mplicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-
   return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=ge
   neric32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-defaul
   t -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -
   Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4436/NVI
   DIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswi
   tch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar 
   -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERN
   EL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DND
   EBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interfac
   e)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4436/NVIDIA-Lin
   ux-x86-185.18.14-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz4436/NVIDIA-
   Linux-x86-185.18.14-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -
   D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/
   include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-r
   eturn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=gen
   eric32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-table
   s -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default
   -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wd
   eclaration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4436/NVIDI
   A-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplic
   it -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer
   -arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qu
   al -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\"
   -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/s
   elfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_os-registry.o /tmp
   /selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4436/NVIDIA-Linu
   x-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfo
   rmat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror 
   -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD
   _MODNAME=KBUILD_STR(nvidia)"  -c -o /t
   mp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/
   selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/
   include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrap
   v -I/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointe
   r-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-q
   ual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\
   " -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME
   =KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/self
   gz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz4
   436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:2025: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/irq.h: En la función ‘irq_to_desc’:
   include/linux/irq.h:189: aviso: comparación entre signed y unsigned
   In file included from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:136: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:139: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     ld -m elf_i386   -r -o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-agp.o /tmp/selfgz4436/N
   VIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-interface.o /tmp/selfgz4436/NVI
   DIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-registry.o /tmp/selfgz4436/NVIDIA
   -Linux-x86-185.18.14-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz4436/NVIDIA-Linux-x
   86-185.18.14-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/u
   sr/src/nv/modules.order
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.28-11-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-11-generic/Modu
   le.symvers -I /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.28-11-generic/Module.markers 
   -M /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D
   __KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/i
   nclude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-re
   turn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=gene
   ric32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-table
   s -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default
   -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wd
   eclaration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4436/NVIDI
   A-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitc
   h -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -W
   error -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL
   __ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEB
   UG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz4436/NVIDIA-Linux-
   x86-185.18.14-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz4436/NVIDIA-Linux-x86-
   185.18.14-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: En l
   a función ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: a
   viso: se usó un puntero de tipo ‘void *’ en la aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
     ld -r -m elf_i386  --build-id -o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.1
   4-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz4436/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   14.914663] type=1505 audit(1248060792.427:4): operation="profile_load"
   name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default"
   pid=1941
   [   14.914709] type=1505 audit(1248060792.427:5): operation="profile_load"
   name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1941
   [   15.059170] type=1505 audit(1248060792.571:6): operation="profile_load"
   name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1946
   [   15.059371] type=1505 audit(1248060792.571:7): operation="profile_load"
   name="/usr/sbin/cupsd" name2="default" pid=1946
   [   15.091466] type=1505 audit(1248060792.603:8): operation="profile_load"
   name="/usr/sbin/tcpdump" name2="default" pid=1950
   [   15.178217] ADDRCONF(NETDEV_UP): eth0: link is not ready
   [   15.180376] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full
   Duplex, Flow Control: RX/TX
   [   15.180606] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
   [   15.946202] NET: Registered protocol family 24
   [   16.681717] ip_tables: (C) 2000-2006 Netfilter Core Team
   [   25.572015] eth0: no IPv6 routers present
   [   30.513449] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
   [   30.513453] Bluetooth: BNEP filters: protocol multicast
   [   30.535701] Bridge firewalling registered
   [   35.485926] rt61pci 0000:02:09.0: firmware: requesting rt2561.bin
   [   35.625389] ADDRCONF(NETDEV_UP): wlan0: link is not ready
   [  297.066281] mtrr: no MTRR for f0000000,8000000 found
   [  531.731758] mtrr: no MTRR for f0000000,8000000 found
   [  577.081572] nvidia: module license 'NVIDIA' taints kernel.
   [  577.089305] NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system
   is
   [  577.089308] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers.
   Please
   [  577.089310] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  577.089312] NVRM:  information.  The 185.18.14 NVIDIA driver will ignore
   [  577.089315] NVRM:  this GPU.  Continuing probe...
   [  577.089388] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```
Someone know what happen ? :/

---

### Post by Whiffle on 2009-07-19
First of all, have you tried using the Restricted Drivers manager thing provided by Ubuntu?  (its under System > Administration).  Its the easiest way to get nvidia going in Linux.

---

### Post by rorrometal on 2009-07-20
Yes, but when the S.O Starts.. Appear a screen something Low-Quality or mode idk :s
i tried too by EnvyNG but the same problem at start up :S

---

### Post by jocko on 2009-07-20
> **rorrometal said:**
> I tried to install nvidia driver but i have this problem.

```
[  577.089305]...
[COLOR=Red]NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system
   is
   [  577.089308] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers.
   Please
   [  577.089310] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  577.089312] NVRM:  information.  The 185.18.14 NVIDIA driver will ignore
   [  577.089315] NVRM:  this GPU.  Continuing probe...
   [  577.089388] NVRM: No NVIDIA graphics adapter found![/COLOR]
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```Someone know what happen ? :/
Did you read the log before you posted it? It says your gpu is not supported by the driver you are trying to install. Install the 173.14 driver instead.
You'll find it in the restricted driver manager (System --> Administration --> Hardware drivers).

---

### Post by old_as_a_fossil on 2009-09-16
> **jocko said:**
> Did you read the log before you posted it? It says your gpu is not supported by the driver you are trying to install. Install the 173.14 driver instead.
You'll find it in the restricted driver manager (System --> Administration --> Hardware drivers).

I'm facing the same error message. I'm not understanding anything at all. Do we have to purchase GPU from the shop? I mean GPU sounds very much like a piece of hardware chip so that's what I assume.  There is no instruction anywhere how to get a GPU.  The link [http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html) precisely mentions only 3 things - driver, development tools, and SDK. Can someone please say exactly what I have to do about the error message 
 "Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.36
         NVIDIA Linux graphics driver installed in this system. "

I have tried with 2 driver files - cudadriver_2.3_linux_32_190.18.run and NVIDIA-Linux-x86-185.18.36-pkg1.run but got the same message.

I'm using a Linux VM:
uname -a
Linux localhost.localdomain 2.6.9-67.ELsmp #1 SMP Wed Nov 7 13:58:04 EST 2007 i686 i686 i386 GNU/Linux

---

### Post by Whiffle on 2009-09-16
> **old_as_a_fossil said:**
> I'm facing the same error message. I'm not understanding anything at all. Do we have to purchase GPU from the shop? I mean GPU sounds very much like a piece of hardware chip so that's what I assume.  There is no instruction anywhere how to get a GPU.  The link [http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html) precisely mentions only 3 things - driver, development tools, and SDK. Can someone please say exactly what I have to do about the error message 
 "Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.36
         NVIDIA Linux graphics driver installed in this system. "

I have tried with 2 driver files - cudadriver_2.3_linux_32_190.18.run and NVIDIA-Linux-x86-185.18.36-pkg1.run but got the same message.

I'm using a Linux VM:
uname -a
Linux localhost.localdomain 2.6.9-67.ELsmp #1 SMP Wed Nov 7 13:58:04 EST 2007 i686 i686 i386 GNU/Linux


If you're running Linux in a VM, you don't need nvidia drivers, as no VM I am aware of simulates an nvidia card.

---

### Post by old_as_a_fossil on 2009-09-16
> **Whiffle said:**
> If you're running Linux in a VM, you don't need nvidia drivers, as no VM I am aware of simulates an nvidia card.
 
So GPU = nvidia card is indeed a piece of hardware.

---

### Post by Whiffle on 2009-09-16
> **old_as_a_fossil said:**
> So GPU = nvidia card is indeed a piece of hardware.

Yep.

---

### Post by old_as_a_fossil on 2009-09-17
Is there an emulator for windows xp or RedHat Linux available for any of the graphic cards listed in [http://www.nvidia.com/object/cuda_learn_products.html](http://www.nvidia.com/object/cuda_learn_products.html)

---

