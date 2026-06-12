---
title: "Installing Nvidia drivers.."
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by nscreed15 on 2009-04-29
Well after troubleshooting and finding out that it was my graphics card preventing me from installing Linux (XFX 8600GTS) I had to take the graphics card out and use onboard video to install.

Now that Ubuntu is up and running I want to use my 8600, but any time I plug it in, the computer will not boot. I am assuming this is a driver issue so I downloaded the latest drivers from nvidia.com

When I run the installer, I get 2 errors. 1 is that I do not have an Nvidia graphics card installed... Is there any way to get around this? 
The other has to do with X-server running. What is this and how can I turn it off?

PS I am still fairly new to Linux

Thanks,
Nate

---

### Post by Kareeser on 2009-04-29
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44) :)

---

### Post by nscreed15 on 2009-04-29
Okay I tried that and it let me try to install it this time but it throws some errors out.


*No precompiled kernel interface was found to match your kernel, ... download from Nvidia ftp site?*
I click yes, and get:
*None found*
It attempts to compile anyways and finishes with this error:
*Unable to load the kernel module 'nvidia.ko'*

Heres the log file:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Apr 29 13:45:37 2009
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
WARNING: You do not appear to have an NVIDIA GPU supported by the 180.51 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 180.51.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
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
   =/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.tmp_versi
   ons ; rm -f /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.tmp_ve
   rsions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-
   pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.nv.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__
    -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include -inc
   lude include/linux/autoconf.h -Iub
   untu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-a
   liasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-fl
   oat -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586
   -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -
   fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch
   /x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -
   fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -
   fwrapv -I/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv -Wall -Wim
   plicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoi
   nter-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-err
   or -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.51\" -UDEBUG -U_DE
   BUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz13084/NVIDIA-Linu
   x-x86-180.51-pkg1/usr/src/nv/.tmp_n
   v.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.nv-vm
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNE
   L__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include 
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -
   ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-s
   se -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-st
   ack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclarat
   ion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz13084/NVIDIA-Linu
   x-x86-180.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-
   multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ 
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.51\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-
   pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/u
   sr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.os-ag
   p.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERN
   EL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferre
   d-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreesta
   nding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-prot
   ector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-afte
   r-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz13084/NVIDIA-Linux-x86-18
   0.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar
   -subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-
   compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_
   STRING=\"180.51\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.tmp_os-agp.o
   /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.os-in
   terface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D
   __KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/i
   nclude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-re
   turn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=gene
   ric32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -
   fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wde
   claration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz13084/NVIDI
   A-Linux-x86-180.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -
   Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werr
   or -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"180.51\" -UDEBUG -U_DEBUG -DNDEBUG -DMODU
   LE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz13084/NVIDIA-Linux-x86-180
   .51-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz13084/NVIDIA-Linux-x86-18
   0.51-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.os-re
   gistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D_
   _KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/in
   clude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-ret
   urn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=gener
   ic32 -ffreestanding -pipe
    -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-ss
   e2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-
   omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement
   -Wno-pointer-sign -fwrapv -I/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/us
   r/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts 
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180
   .51\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASE
   NAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o 
   /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.tmp_os-registry.o 
   /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.nv-i2
   c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERN
   EL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -
   ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-s
   se -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-st
   ack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclarat
   ion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz13084/NVIDIA-Linu
   x-x86-180.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wforma
   t -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD
   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_V
   ERSION_STRING=\"180.51\" -UDE
   BUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1308
   4/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz13084/NVI
   DIA-Linux-x86-180.51-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.nvacp
   i.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERN
   EL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -
   ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-s
   se -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/
   mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/sel
   fgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-t
   ype -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-m
   ultichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"180.51\" -UDEBUG -U_DEBUG -DNDEBUG -DMO
   DULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-
   pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/
   usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:87,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nv-linux.h:113,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/s
   rc/nv/nvidia.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/nv-k
   ernel.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/nv.o /tmp/s
   elfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz13084/
   NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/os-agp.o /tmp/selfgz13084/NVIDIA-Lin
   ux-x86-180.51-pkg1/usr/src/nv/os-interface.o /tmp/selfgz13084/NVIDIA-Linux-x
   86-180.51-pkg1/usr/src/nv/os-registry.o /tmp/selfgz13084/NVIDIA-Linux-x86-18
   0.51-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/
   usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/
   usr/src/nv/nvidia.ko;) > /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/s
   rc/nv/modules.order
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.28-11-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-11-generic/Modu
   le.symvers -I /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/Modul
   e.symvers  -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/Modul
   e.symvers -S -K /usr/src/linux-headers-2.6.28-11-generic/Module.markers -M /
   tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/
   usr/src/nv/Module.markers -w  -s
   WARNING: could not find /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/sr
   c/nv/.nv-kernel.o.cmd for /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/
   src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/.nvidi
   a.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__
   KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/inc
   lude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impli
   cit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generi
   c32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -
   mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -f
   no-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdec
   laration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/se
   lfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-
   multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ 
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.51\" -UDEBUG -U_DEBUG -DNDEBUG  -D
   "KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz13084/NVIDIA-Linux-x86-1
   80.51-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-
   pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/
   nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-
   pkg1/usr/src/nv/nvidia.ko /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/
   src/nv/nvidia.o /tmp/selfgz13084/NVIDIA-Linux-x86-180.51-pkg1/usr/src/nv/nvi
   dia.mod.o
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
   [ 1327.264192] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 1336.165519] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 2786.296389] mtrr: no MTRR for 80000000,10000000 found
   [ 2787.087688] [drm:i915_setparam] *ERROR* unknown parameter 4
   [ 2787.087718] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 2787.620562] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 2796.804870] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3042.805665] mtrr: no MTRR for 80000000,10000000 found
   [ 3139.581810] [drm:i915_setparam] *ERROR* unknown parameter 4
   [ 3139.581838] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3140.115649] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3148.528565] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3316.903196] mtrr: no MTRR for 80000000,10000000 found
   [ 3383.231772] nvidia: module license 'NVIDIA' taints kernel.
   [ 3383.237833] NVRM: No NVIDIA graphics adapter found!
   [ 3419.551076] [drm:i915_setparam] *ERROR* unknown parameter 4
   [ 3419.551105] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3420.082243] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3428.504199] [drm:i915_getparam] *ERROR* Unknown parameter 6
   [ 3585.131368] mtrr: no MTRR for 80000000,10000000 found
   [ 3650.867904] NVRM: No NVIDIA graphics adapter found!
   [ 3703.576377] glxinfo[12822]: segfault at 0 ip 0804ad46 sp bf85e7d0 error 4
   in glxinfo[8048000+5000]
   [ 3703.610937] glxinfo[12825]: segfault at 0 ip 0804ad46 sp bf80cf60 error 4
   in glxinfo[8048000+5000]
   [ 3785.731175] mtrr: no MTRR for 80000000,10000000 found
   [ 3880.400997] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Nate

---

### Post by nscreed15 on 2009-04-29
Bump

---

### Post by stchman on 2009-04-29
Sounds like something is wrong with your graphics card.  Your PC should be able to boot with the video card.

I have an 8800GT and 7600GT both work very well in Linux.

---

### Post by Kareeser on 2009-04-29
Indeed... that's a pretty weird error message. The supported products list shows your card (8600GTS) as being supported.

The script also tells you if you've downloaded the wrong architecture, so that's not the culprit here...

It's normal for the "check for kernel modules online?" step to fail. As a fallback, the driver compiles its own, which usually works.

This link may give you some insight: [http://www.nvnews.net/vbulletin/showthread.php?t=49951](http://www.nvnews.net/vbulletin/showthread.php?t=49951)

---

### Post by nscreed15 on 2009-05-01
Problem solved:P Computer randomly let me boot with the graphics card installed (lol) and I was able to install the drivers.

---

