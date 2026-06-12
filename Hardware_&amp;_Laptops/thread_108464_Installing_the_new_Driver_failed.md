---
title: "Installing the new Driver failed"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by imranj on 2005-12-26
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Dec 26 04:17:16 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> There appears to already be a driver installed on your system (version: 1.0-
   8174).  As part of installing this driver (version: 1.0-8178), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC test with CC="gcc-4.0".
-> Kernel source path: '/lib/modules/2.6.14-ck1/source'
-> Kernel output path: '/lib/modules/2.6.14-ck1/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.14-ck1/sour
   ce SYSOUT=/lib/modules/2.6.14-ck1/build'...
   
   NVIDIA: calling KBUILD...
   make CC=gcc-4.0 KBUILD_OUTPUT=/lib/modules/2.6.14-ck1/build KBUILD_VERBOSE=1
   -C /lib/modules/2.6.14-ck1/source SUBDIRS=/tmp/selfgz11574/NVIDIA-Linux-x86-
   1.0-8178-pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.14-ck1/build \
   KBUILD_SRC=/usr/src/linux-2.6.14cK1 \
   KBUILD_EXTMOD="/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv" -
   f /usr/src/linux-2.6.14cK1/Makefile modules
   mkdir -p /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/.tmp_ver
   sions
   make -f /usr/src/linux-2.6.14cK1/scripts/Makefile.build obj=/tmp/selfgz11574
   /NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`gcc-4.0 -v 2>&1 | tail -n 1`\" > /tmp/selfgz115
   74/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv_compiler.h
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__K
   ERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include  -I/tmp/self
   gz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/n
   v -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno
   -common -ffreestanding -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferr
   ed-stack-boundary=2 -fno-unit-at-a-time -march=athlon -I/usr/src/linux-2.6.1
   4cK1/include/asm-i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclara
   tion-after-statement -Wno-pointer-sign  -I/tmp/selfgz11574/NVIDIA-Linux-x86-
   1.0-8178-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -fno
   -common -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -
   D__KERNEL__ -DMODULE -DNTRM -DNVRM -DDYNAMIC_SLI -DNV_MAJOR_VERSION=1 -DNV_M
   INOR_VERSION=0 -DNV_PATCHLEVEL=8178 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_ST
   RUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -D
   NV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAG
   E_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MO
   DNAME=nvidia -c -o /tmp/selfgz11574/
   NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz11574/NVIDIA-
   Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:339: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:448,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c: At top leve
   l:
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c:296: warning
   : initialization from incompatible pointer type
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c: In function
   ‘nvidia_init_module’:
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c:1305: warnin
   g: ‘pm_register’ is deprecated (declared at include/linux/pm.h:107)
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c:1423: warnin
   g: ‘pm_unregister’ is deprecated (declared at include/linux/pm.h:112)
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c: In function
   ‘nvidia_exit_module’:
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv.c:1479: warnin
   g: ‘pm_unregister’ is deprecated (declared at include/linux/pm.h:112)
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D
   __KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include  -I/tmp/s
   elfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O
   2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-
   unit-at-a-time -march=athlon -I/usr/src/linux-2.6.14cK1/include/asm-i386/mac
   h-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno
   -pointer-sign  -I/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv 
   -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -O -fno-common -MD -Wsign-compare -Wno-cast-qual -Wno-error -
   D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -DNVRM -DDYNAMIC_SLI -DNV_
   MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8178 -UDEBUG -U_DEBUG -
   DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PC
   I_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_REMAP_PFN_RANGE_P
   RESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODULE -DKBUILD_B
   ASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz11574/NVIDIA-Linux-x8
   6-1.0-8178-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.
   0-8178-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:339: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:448,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -
   D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include  -I/tmp/
   selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -
   O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno
   -unit-at-a-time -march=athlon -I/usr/src/linux-2.6.14cK1/include/asm-i386/ma
   ch-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wn
   o-pointer-sign  -I/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -O -fno-common -MD -Wsign-compar
   e -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNT
   RM -DNVRM -DDYNAMIC_SLI -DNV_MAJOR_VERSION=1 -DNV
   _MINOR_VERSION=0 -DNV_PATCHLEVEL=8178 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_
   STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT 
   -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_P
   AGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODULE -DKBUILD_BASENAME=os_agp -DKBU
   ILD_MODNAME=nvidia -c -o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr
   /src/nv/.tmp_os-agp.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-agp.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:339: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:448,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/inc
   lude -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include  -
   I/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestan
   ding -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=
   2 -fno-unit-at-a-time -march=athlon -I/usr/src/linux-2.6.14cK1/include/asm-i
   386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-stateme
   nt -Wno-pointer-sign  -I/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/
   src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -O -fno-common -MD -Wsign
   -compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODU
   LE -DNTRM -DNVRM -DDYNAMIC_SLI -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DN
   V_PATCHLEVEL=8178 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MUL
   TIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_
   COUNT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR
   _PRESENT -DNV_VMAP_4_PRESENT -DMODULE -DKBUILD_BASENAME=os_interface -DKBUIL
   D_MODNAME=nvidia -c -o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/s
   rc/nv/.tmp_os-interface.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/us
   r/src/nv/os-interface.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:339: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:448,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.os-registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/incl
   ude -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include  -I
   /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestand
   ing -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2
   -fno-unit-at-a-time -march=athlon -I/usr/src/linux-2.6.14cK1/include/asm-i38
   6/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement
   -Wno-pointer-sign  -I/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -O -fno-common -MD -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE 
   -DNTRM -DNVRM -DDYNAMIC_SLI -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_P
   ATCHLEVEL=8178 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIP
   LE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COU
   NT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_V
   MAP_4_PRESENT -DMODULE -DKBUILD_BASENAME=os_registry -DKBUILD_MODNAME=nvidia
   -c -o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/.tmp_os-reg
   istry.o /tmp/selfgz11574/NVIDIA-L
   inux-x86-1.0-8178-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:77,
                    from include/linux/kernel.h:15,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:46,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/asm/bitops.h: In function ‘find_first_bit’:
   include/asm/bitops.h:339: warning: comparison between signed and unsigned
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:47,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:448,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/nv-linux.h:71,
                    from /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-81
   78-pkg1/usr/src/nv/nvidia.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/
   usr/src/nv/nv-kernel.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/s
   rc/nv/nv.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv-vm.
   o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-agp.o /tmp/s
   elfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-interface.o /tmp/sel
   fgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-2.6.14cK1/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-2.6.14cK1/Module.symvers vmlin
   ux /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/
   usr/src/nv/nv-kernel.o
     gcc-4.0 -Wp,-MD,/tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv
   /.nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/inclu
   de -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.14cK1/include -I/u
   sr/src/linux-2.6.14cK1/ -I -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs 
   -fno-strict-aliasing -fno-common -ffreestanding -O2 -fomit-frame-pointer -pi
   pe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=athl
   on -I/usr/src/linux-2.6.14cK1/include/asm-i386/mach-default -Iinclude/asm-i3
   86/mach-default -Wdeclaration-after-statement -Wno-pointer-sign  -DKBUILD_BA
   SENAME=nvidia -DKBUILD_MODNAME=nvidia -DMODULE -c -o /tmp/selfgz11574
   /NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz11574/NVI
   DIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-817
   8-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz11574/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 File exists
-> Kernel messages:
   [4311848.629000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=209.197.105.94
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=37821 PROTO=TCP
   SPT=80 DPT=59392 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311852.329000] nvidia: version magic '2.6.14-ck1 K7 gcc-3.4' should be
   '2.6.14-ck1 K7 gcc-4.0'
   [4311857.288000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.250.103
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=53369 DF PROTO=TCP
   SPT=2556 DPT=139 WINDOW=18528 RES=0x00 SYN URGP=0 
   [4311860.140000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.250.103
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=53536 DF PROTO=TCP
   SPT=2556 DPT=139 WINDOW=18528 RES=0x00 SYN URGP=0 
   [4311886.044000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=35709 PROTO=TCP
   SPT=80 DPT=44787 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311891.437000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.236.38
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=11122 DF PROTO=TCP
   SPT=1526 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0 
   [4311894.212000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.236.38
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=11686 DF PROTO=TCP
   SPT=1526 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0 
   [4311895.988000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=64.233.161.184
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=29299 PROTO=TCP
   SPT=80 DPT=49764 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311909.654000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.73.188
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=4623 DF PROTO=TCP
   SPT=1487 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
   [4311912.600000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=217.164.73.188
   DST=217.164.172.215 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=5087 DF PROTO=TCP
   SPT=1487 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
   [4311915.545000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=66.35.250.62
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=61334 PROTO=TCP
   SPT=80 DPT=33803 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311920.119000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=8498 PROTO=TCP
   SPT=80 DPT=44789 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311920.119000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=8499 PROTO=TCP
   SPT=80 DPT=44785 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311920.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.133.142
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=36842 PROTO=TCP
   SPT=80 DPT=51322 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311920.619000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=11908 PROTO=TCP
   SPT=80 DPT=44786 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311920.739000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=66.150.87.2
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=38698 PROTO=TCP
   SPT=80 DPT=44433 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311921.119000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=21747 PROTO=TCP
   SPT=80 DPT=44788 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311921.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=165.21.32.104
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=40711 PROTO=TCP
   SPT=80 DPT=45740 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311921.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=209.197.107.132
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=40718 PROTO=TCP
   SPT=80 DPT=51461 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311921.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=209.197.107.132
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=40719 PROTO=TCP
   SPT=80 DPT=51460 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311921.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=209.197.107.132
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=40720 PROTO=TCP
   SPT=80 DPT=51459 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311922.239000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=165.21.32.104
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=44823 PROTO=TCP
   SPT=80 DPT=45744 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311922.739000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=66.150.87.2
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=46860 PROTO=TCP
   SPT=80 DPT=44435 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311923.120000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=65.181.171.172
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=60226 PROTO=TCP
   SPT=80 DPT=44784 WINDOW=65535 RES=0x00 ACK URGP=0 
   [4311923.770000] Inbound IN=eth0 OUT=
   MAC=00:0c:76:e1:48:ae:00:30:b8:c2:d7:90:08:00 SRC=209.197.105.94
   DST=217.164.172.215 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=18010 PROTO=TCP
   SPT=80 DPT=59392 WINDOW=65535 RES=0x00 ACK URGP=0 
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

