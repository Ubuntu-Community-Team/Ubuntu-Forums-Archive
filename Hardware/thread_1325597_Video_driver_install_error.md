---
title: "Video driver install error"
date: 2009-11-13
forum: Hardware
---

### Post by Liliitha on 2009-11-13
I got the latest driver from NVIDIA, NVIDIA-Linux-x86-185.18.14-pkg1.run
I do the following but get a bad error message :(

Alt-Ctrl-F1

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-185.18.14
It loads up, asks me to accept it's agreement then goes on to say I don't have the kernel.  I tell it to build one and it says it failed at building the kernel and then the installation aborts.  Any ideas as to what this is?  Here is the error log.

> vidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Nov 13 15:35:37 2009
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.18.14.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.31-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.31-14-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.31-14-gener
   ic/build SYSOUT=/lib/modules/2.6.31-14-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-14-generic/build SUBDIRS
   =/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.1
   4-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude
    -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubunt
   u/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-for
   mat-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm
   =3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=gener
   ic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-a
   ll -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3586/NVIDIA-Linux-x86-185.18
   .14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-p
   op -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM
   -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=
   KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz358
   6/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz3586/NVIDI
   A-Linux-x86-185.18.14-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -Wno-format-security -fno-delete-null-pointer-checks -
   O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bound
   ary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024
   -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-stat
   ement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/self
   gz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-d
   efer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE 
   -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAM
   E=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1
   /usr/src/nv/.tmp_nv-vm.o /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr
   /src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3586/NVIDIA-Linux-x86-185.
   18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer
   -pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/u
   sr/src/nv/.tmp_os-agp.o /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/
   src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-agp.c: In func
   tion ‘KernLoadAGPPages’:
   /tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-agp.c:296: err
   or: ‘agp_memory’ has no member named ‘memory’
   make[3]: *** [/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-
   agp.o] Error 1
   make[2]: *** [_module_/tmp/selfgz3586/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

