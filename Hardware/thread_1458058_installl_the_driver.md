---
title: "installl the driver"
date: 2010-04-19
forum: Hardware
---

### Post by apachemaven on 2010-04-19
HI:
I can not open the visual effect,so I tried to install the driver from the nvdia.com.

I download the NVIDIA-Linux-x86-195.36.15-pkg1.run.

Then I stop the Xserver, and run the script,however it tell me the nvdia.ko can not found.

what is going on?

The logs:
0----------------------
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Apr 20 01:11:27 2010
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
-> License accepted.
-> Installing NVIDIA driver version 195.36.15.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-21-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-21-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.32-21-gener
   ic/build SYSOUT=/lib/modules/2.6.32-21-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.1
   5-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude
    -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration 
   -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -
   mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtu
   ne=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -f
   stack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-
   sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mn
   o-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x8
   6-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/se
   lfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz211
   1/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv_
   gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_nv_gvi.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-
   null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-
   args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195
   .36.15\" -UDEBUG -U_DEBUG -DNDEBUG 
    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.
   36.15-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.1
   5-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-la
   rger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_os-agp.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CF
   I_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-
   pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tm
   p/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
   -Wno-multicha
   r -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KE
   RNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -D
   NDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_inter
   face)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2111/NVIDIA-
   Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz2111/NVID
   IA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregp
   arm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=ge
   neric -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-
   compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dn
   ow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-ca
   lls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow
   -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-195.
   36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer
   -pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-p
   kg1/usr/src/nv/.tmp_os-registry.o /
   tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x8
   6-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNA
   ME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg
   1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D
   __KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -Werror-implicit-function-declaration -Wno-format-security 
   -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-stru
   ct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumula
   te-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCON
   FIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-large
   r-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclar
   ation-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi
   -asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/
   src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign
   -compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION
   _STRING=\"195.36.15\" -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nva
   cpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2111/NVIDIA-L
   inux-x86-195.36.15-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz2111/NVIDIA-Linu
   x-x86-195.36.15-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   11/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi.o /tmp/sel
   fgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz2111/N
   VIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp.o /tmp/selfgz2111/NVIDIA-Li
   nux-x86-195.36.15-pkg1/usr/src/nv/os-interface.o /tmp/selfgz2111/NVIDIA-Linu
   x-x86-195.36.15-pkg1/usr/src/nv/os-registry.o /tmp/selfgz2111/NVIDIA-Linux-x
   86-195.36.15-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.3
   6.15-pkg1/usr/src/
   nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.32-21-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-21-generic/Modu
   le.symvers -I /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/M
   odule.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraph
   s -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wn
   o-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mre
   gparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=
   generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fsta
   ck-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overfl
   ow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2111/NVIDIA-Linux-x86-1
   95.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-de
   fer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -
   DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /t
   mp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvidia.mod.o /tmp/s
   elfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-21-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/
   usr/src/nv/nvidia.ko /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src
   /nv/nvidia.o /tmp/selfgz2111/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvid
   ia.mod.o
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
   [   51.684942] wlan0: direct probe to AP 00:27:19:6a:5a:04 (try 1)
   [   51.690163] wlan0: direct probe responded
   [   51.690169] wlan0: authenticate with AP 00:27:19:6a:5a:04 (try 1)
   [   51.694494] wlan0: authenticated
   [   51.694519] wlan0: associate with AP 00:27:19:6a:5a:04 (try 1)
   [   51.696352] wlan0: RX AssocResp from 00:27:19:6a:5a:04 (capab=0x431
   status=0 aid=2)
   [   51.696355] wlan0: associated
   [   51.697057] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
   [   61.756036] wlan0: no IPv6 routers present
   [   88.504046] Clocksource tsc unstable (delta = -227307268 ns)
   [  197.945062] wlan0: deauthenticating from 00:27:19:6a:5a:04 by local
   choice (reason=3)
   [  197.957199] [drm] nouveau 0000:02:00.0: nouveau_channel_free: freeing
   fifo 2
   [  198.399577] [drm] nouveau 0000:02:00.0: Allocating FIFO number 2
   [  198.402607] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc:
   initialised FIFO 2
   [  230.303834] [drm] nouveau 0000:02:00.0: nouveau_channel_free: freeing
   fifo 2
   [  275.070622] nvidia: module license 'NVIDIA' taints kernel.
   [  275.070627] Disabling lock debugging due to kernel taint
   [  276.425282] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  276.425287] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  276.425289] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  276.425290] NVRM: device(s).
   [  276.425293] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  276.425295] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  276.425296] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  276.425299] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```-----------------------------

---

### Post by hsoulen on 2010-04-22
Hi, looks to me like your kernel source may be the problem.

Seems you are running the Lucid beta, could you maybe have run into a "Partial upgrade" in update manager?

Run "uname -r" and post your kernel version and we can try and troubleshoot from there.

Hank

---

### Post by apachemaven on 2010-04-24
> **hsoulen said:**
> Hi, looks to me like your kernel source may be the problem.

Seems you are running the Lucid beta, could you maybe have run into a "Partial upgrade" in update manager?

Run "uname -r" and post your kernel version and we can try and troubleshoot from there.

Hank
Thanks.
I will post the required information when I at home.

---

### Post by apachemaven on 2010-04-24
> **hsoulen said:**
> Hi, looks to me like your kernel source may be the problem.

Seems you are running the Lucid beta, could you maybe have run into a "Partial upgrade" in update manager?

Run "uname -r" and post your kernel version and we can try and troubleshoot from there.

Hank

Yes, I install the 10.04 beta directly using the "ubuntu-10.04-beta2-desktop-i386"

The output of the "uname -r" is :2.6.32-21-generic.

And I have update my system to the latest using the update manager.

So is there other information required?

---

### Post by hsoulen on 2010-04-25
OK Great, now let's just make sure your kernel source is installed.

Run the Synaptic Package Manager (under System->Administration) and make sure the package "linux-headers-2.6.32-21-generic" is installed (the tic-box next to it will be green).

If all is well there the next question I have is how you are running the installer, officialy the installer is not supported (see the Beta notes here: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2) see the "Known Issues section) but it works for me with a few warnings and for other folks as well.

If you are running gnome I am assuming you are exiting gnome with "sudo gdm-stop" is this correct? Now when running the Nvidia driver installer you should not have it on the desktop, you should save it to a directory under your home folder (e.g. /home/hank/drivers) and run it from there, last thing with the installer is that I find running it with "sudo ./Nvidia-XXXX" sometimes causes me issue, so I run "sudo su" enter my password then run the driver "./Nvidia-XXXX".

Let me know if this all works for you, and make sure that if your log looks clean and the install seemed to work but you still cannot enable desktop effects, run "System->Administration->Hardware Drivers" and make sure the correct driver is enabled.

Good luck.

Hank

---

### Post by apachemaven on 2010-04-28
> **hsoulen said:**
> OK Great, now let's just make sure your kernel source is installed.

Run the Synaptic Package Manager (under System->Administration) and make sure the package "linux-headers-2.6.32-21-generic" is installed (the tic-box next to it will be green).

If all is well there the next question I have is how you are running the installer, officialy the installer is not supported (see the Beta notes here: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2) see the "Known Issues section) but it works for me with a few warnings and for other folks as well.

If you are running gnome I am assuming you are exiting gnome with "sudo gdm-stop" is this correct? Now when running the Nvidia driver installer you should not have it on the desktop, you should save it to a directory under your home folder (e.g. /home/hank/drivers) and run it from there, last thing with the installer is that I find running it with "sudo ./Nvidia-XXXX" sometimes causes me issue, so I run "sudo su" enter my password then run the driver "./Nvidia-XXXX".

Let me know if this all works for you, and make sure that if your log looks clean and the install seemed to work but you still cannot enable desktop effects, run "System->Administration->Hardware Drivers" and make sure the correct driver is enabled.

Good luck.

Hank

It does not work.

THe logs:

------------------
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Apr 28 23:35:10 2010
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
-> License accepted.
-> Installing NVIDIA driver version 195.36.15.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-21-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-21-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.32-21-gener
   ic/build SYSOUT=/lib/modules/2.6.32-21-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.1
   5-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude
    -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration 
   -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -
   mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtu
   ne=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -f
   stack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-
   sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mn
   o-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x8
   6-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/se
   lfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz184
   2/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv_
   gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_nv_gvi.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-
   null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-
   args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195
   .36.15\" -UDEBUG -U_DEBUG -DNDEBUG 
    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.
   36.15-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.1
   5-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-la
   rger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.tm
   p_os-agp.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CF
   I_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-
   pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tm
   p/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
   -Wno-multicha
   r -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KE
   RNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -D
   NDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_inter
   face)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1842/NVIDIA-
   Linux-x86-195.36.15-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz1842/NVID
   IA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-interface.c:26:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregp
   arm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=ge
   neric -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-
   compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dn
   ow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-ca
   lls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow
   -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-195.
   36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer
   -pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-p
   kg1/usr/src/nv/.tmp_os-registry.o /
   tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/os-registry.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x8
   6-195.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNA
   ME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg
   1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D
   __KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -Werror-implicit-function-declaration -Wno-format-security 
   -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-stru
   ct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumula
   te-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCON
   FIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-large
   r-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclar
   ation-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi
   -asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/
   src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign
   -compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION
   _STRING=\"195.36.15\" -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nva
   cpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1842/NVIDIA-L
   inux-x86-195.36.15-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz1842/NVIDIA-Linu
   x-x86-195.36.15-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvacpi.c:15:
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
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz18
   42/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv_gvi.o /tmp/sel
   fgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz1842/N
   VIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/os-agp.o /tmp/selfgz1842/NVIDIA-Li
   nux-x86-195.36.15-pkg1/usr/src/nv/os-interface.o /tmp/selfgz1842/NVIDIA-Linu
   x-x86-195.36.15-pkg1/usr/src/nv/os-registry.o /tmp/selfgz1842/NVIDIA-Linux-x
   86-195.36.15-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.3
   6.15-pkg1/usr/src/
   nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.32-21-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-21-generic/Modu
   le.symvers -I /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/M
   odule.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraph
   s -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wn
   o-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mre
   gparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=
   generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fsta
   ck-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overfl
   ow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1842/NVIDIA-Linux-x86-1
   95.36.15-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-de
   fer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -
   DNVRM -DNV_VERSION_STRING=\"195.36.15\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /t
   mp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvidia.mod.o /tmp/s
   elfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-21-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/
   usr/src/nv/nvidia.ko /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src
   /nv/nvidia.o /tmp/selfgz1842/NVIDIA-Linux-x86-195.36.15-pkg1/usr/src/nv/nvid
   ia.mod.o
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
   [   28.765138] input: HDA Digital PCBeep as
   /devices/pci0000:00/0000:00:07.0/input/input11
   [   67.395492] wlan0: direct probe to AP 00:27:19:6a:5a:04 (try 1)
   [   67.395579] wlan0: deauthenticating from 00:27:19:6a:5a:04 by local
   choice (reason=3)
   [   67.395605] wlan0: direct probe to AP 00:27:19:6a:5a:04 (try 1)
   [   67.398673] wlan0: direct probe responded
   [   67.398679] wlan0: authenticate with AP 00:27:19:6a:5a:04 (try 1)
   [   67.401499] wlan0: authenticated
   [   67.401524] wlan0: associate with AP 00:27:19:6a:5a:04 (try 1)
   [   67.403643] wlan0: RX AssocResp from 00:27:19:6a:5a:04 (capab=0x431
   status=0 aid=3)
   [   67.403647] wlan0: associated
   [   67.404639] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
   [   74.329059] wlan0: deauthenticating from 00:27:19:6a:5a:04 by local
   choice (reason=3)
   [   74.348946] [drm] nouveau 0000:02:00.0: nouveau_channel_free: freeing
   fifo 2
   [   78.212073] wlan0: no IPv6 routers present
   [   86.504116] Clocksource tsc unstable (delta = -90687485 ns)
   [  130.444384] nvidia: module license 'NVIDIA' taints kernel.
   [  130.444389] Disabling lock debugging due to kernel taint
   [  131.801947] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  131.801952] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  131.801954] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  131.801955] NVRM: device(s).
   [  131.801958] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  131.801960] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  131.801961] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  131.801964] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```
---------------------

I give up.

---

### Post by mothes on 2010-04-30
I have the same problem and the same log file. 
I installed Ubuntu 10.04 LTS it's not beta or alfa. 

This is text of error: 

**Error: **
"Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used build the target kernel, or if a driver sush as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NDVIDIA graphics device or NVIDIA GPU installed in this system is not supported bu this graphics driver release."

---

### Post by hsoulen on 2010-05-03
Have you guys tried just installing the drivers from the Ubuntu restricted ppa using Synaptic? Or even the old command line?

```
sudo apt-get install nvidia-current
```Configure:

```
sudo nvidia-xconfig
```As far as I know the Nvidia installer is still not "officially" supported in Lucid, I think it may have something to do with the default nv driver having been replaced with nouveau. If this is a brand-new 10.04 LTS install (no Alpha/Beta or Karmic upgrade) then I think this might be the issue.

Oh I forgot, after you install the Nvidia driver from restricted you may need to go to System->Administration->Hardware Drivers and select the desired driver to get it workin.

Cheers,

Hank

---

