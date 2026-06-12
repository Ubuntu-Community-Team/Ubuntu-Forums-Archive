---
title: "nvidia"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Magni on 2006-12-27
hi@all

i´ve tried to install the nvidia-driver on my notebook, a fujitsu siemens celsius mobile h. [i used this howto]("http://ubuntuforums.org/showthread.php?t=263851")

have anyone installed the nvidia-driver for this card:
```
01:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro4 500 GoGL] (rev a3)

```

kern.log:
```
Dec 27 23:13:08 Asgard kernel: [17185315.036000] nvidia: disagrees about version of symbol struct_module
```

here is my nvidia-installer log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Dec 27 23:12:38 2006

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
WARNING: The NVIDIA Quadro4 500 GoGL GPU installed in this system is supported
         through the NVIDIA 1.0-96xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 1.0-9746 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-9746
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         www.nvidia.com.
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/usr/src/linux'
-> Kernel output path: '/usr/src/linux'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux SYSOUT=/usr/s
   rc/linux'...
   sh ./conftest.sh "cc" "cc" /usr/src/linux /usr/src/linux cc_sanity_check ful
   l_output
   sh ./conftest.sh "cc" "cc" /usr/src/linux /usr/src/linux select_makefile ful
   l_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux SUBDIRS=/tmp/selfgz9891/NVIDI
   A-Linux-x86-1.0-9746-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.tmp_vers
   ions
   rm -f /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.tmp_version
   s/*
   make -f scripts/Makefile.build obj=/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz9891/NVI
   DIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL_
   _ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-com
   mon -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tabl
   es -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=gener
   ic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-
   after-statement -Wno-pointer-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-974
   6-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-com
   mon -msoft-float       -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOO
   SE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINO
   R_VERSION=0 -DNV_PATCHLEVEL=9746  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRU
   CT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV
   _SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER_WIT
   H_PTREGS_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -
   DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_
   PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESEN
   T  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-97
   46-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/
   usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERN
   EL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector
   -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestan
   ding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-poin
   ter-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith  -Wno-multichar  -Werror  -O -fno-common -msoft-float       -M
   D   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNE
   L__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEV
   EL=9746  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRI
   DGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRE
   SENT -DNV_PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER_WITH_PTREGS_PRESENT -DNV_PCI
   _CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOIN
   T_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VM
   AP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv
   _vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9891/NVIDIA-Li
   nux-x86-1.0-9746-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz9891/NVIDIA-Linux-x
   86-1.0-9746-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protecto
   r -O2 -fomit-frame-pointer -fasynchronous-unwind-ta
   bles -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=gen
   eric -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaratio
   n-after-statement -Wno-pointer-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9
   746-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-c
   ommon -msoft-float       -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_L
   OOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MI
   NOR_VERSION=0 -DNV_PATCHLEVEL=9746  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_ST
   RUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -D
   NV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER_W
   ITH_PTREGS_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT
   -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE
   _PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBU
   ILD_BASENAME=KBUILD_STR(os_agp)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9891/NVIDIA-Linux-x86-
   1.0-9746-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-
   9746-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-pr
   otector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-f
   loat -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -f
   freestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -
   Wno-pointer-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-common -msoft-float  
       -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D_
   _KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_
   MINOR_VERSION=0 -DNV_PATCHLEVEL=9746  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_
   STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT 
   -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER
   _WITH_PTREGS_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESE
   NT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHA
   NGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvid
   ia)" -c -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.tmp_os
   -interface.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/os-in
   terface.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.os-r
   egistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-pro
   tector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -p
   ipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -m
   regparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after
   -statement -Wno-pointer-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg
   1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscri
   pts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror  -O -fno-common -
   msoft-float       -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KE
   RNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VER
   SION=0 -DNV_PATCHLEVEL=9746  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RL
   IM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSC
   TL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER_WITH_PTR
   EGS_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_O
   LD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_
   ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BA
   SENAME=KBUILD_STR(os_registry)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.
   0-9746-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz9891/NVIDIA-Linux-x86-1
   .0-9746-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.nv-i
   2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protecto
   r -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -
   mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreest
   anding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-po
   inter-sign -I/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv -Wall
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith  -Wno-multichar  -Werror  -O -fno-common -msoft-float       -
   MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERN
   EL__ -DMODULE  -DNVRM -DNV_MAJOR_VER
   SION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9746  -UDEBUG -U_DEBUG -DNDEBUG 
   -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CL
   ***_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV
   _IRQ_HANDLER_WITH_PTREGS_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSER
   T_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRES
   ENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)" -c -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.
   tmp_nv-i2c.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/nv-i2
   c.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src
   /nv/nv-i2c.c:8:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-974
   6-pkg1/usr/src/nv/nvidia.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/us
   r/src/nv/nv-kernel.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/
   nv/nv.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/nv-vm.o /t
   mp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/os-agp.o /tmp/selfgz
   9891/NV
   IDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/os-interface.o /tmp/selfgz9891/NVIDI
   A-Linux-x86-1.0-9746-pkg1/usr/src/nv/os-registry.o /tmp/selfgz9891/NVIDIA-Li
   nux-x86-1.0-9746-pkg1/usr/src/nv/nv-i2c.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpos
   t
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-generic/Modu
   le.symvers -I /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/Modu
   les.symvers -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/Mod
   ules.symvers /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/nvidi
   a.o
   WARNING: could not find /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/.nvid
   ia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D_
   _KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-prot
   ector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-flo
   at -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffr
   eestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wn
   o-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz9891/NVID
   IA-Linux-x86-1.0-9746-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz9891/NVIDIA-Li
   nux-x86-1.0-9746-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746
   -pkg1/usr/src/nv/nvidia.ko /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/us
   r/src/nv/nvidia.o /tmp/selfgz9891/NVIDIA-Linux-x86-1.0-9746-pkg1/usr/src/nv/
   nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   [17185062.488000] printk: 11 messages suppressed.
   [17185062.488000] eth1: Information frame lost.
   [17185067.300000] printk: 10 messages suppressed.
   [17185067.300000] eth1: Information frame lost.
   [17185072.416000] printk: 11 messages suppressed.
   [17185072.416000] eth1: Information frame lost.
   [17185077.332000] printk: 11 messages suppressed.
   [17185077.332000] eth1: Information frame lost.
   [17185082.348000] printk: 11 messages suppressed.
   [17185082.348000] eth1: Information frame lost.
   [17185087.468000] printk: 11 messages suppressed.
   [17185087.468000] eth1: Information frame lost.
   [17185092.584000] printk: 11 messages suppressed.
   [17185092.584000] eth1: Information frame lost.
   [17185097.396000] printk: 10 messages suppressed.
   [17185097.396000] eth1: Information frame lost.
   [17185102.620000] printk: 11 messages suppressed.
   [17185102.620000] eth1: Information frame lost.
   [17185107.432000] printk: 10 messages suppressed.
   [17185107.432000] eth1: Information frame lost.
   [17185112.548000] printk: 11 messages suppressed.
   [17185112.548000] eth1: Information frame lost.
   [17185191.556000] eth1: New link status: AP Out of Range (0004)
   [17185191.844000] eth1: New link status: AP In Range (0005)
   [17185315.036000] nvidia: disagrees about version of symbol struct_module
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

do you need more infos?

---

### Post by PurplePenguin on 2006-12-27
Looks like this (below, quoted) is pretty important. It seems as if your gpu is supported not by the 97xx drivers, but the 96xx ones.  If I were you, I'd try to install the older drivers.

```
WARNING: The NVIDIA Quadro4 500 GoGL GPU installed in this system is supported
         through the NVIDIA 1.0-96xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 1.0-9746 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-9746
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         www.nvidia.com.
```

---

### Post by Magni on 2006-12-28
:D okay, i try it

but in the 97xx drivers i found my chip under supported GPUs (Quadro4 500 GoGL 	0x017C). in 1h i post my results

thanks

---

### Post by Magni on 2006-12-28
perfect, i´ve a new error message :D

uname -r
```
2.6.17-10-386
```

nvidia-kernel.log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Dec 28 13:26:45 2006

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
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/usr/src/linux'
-> Kernel output path: '/usr/src/linux'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux SYSOUT=/usr/s
   rc/linux'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux SUBDIRS=/tmp/selfgz7939/NVIDI
   A-Linux-x86-1.0-9631-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/.tmp_vers
   ions
   rm -f /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/.tmp_version
   s/*
   
     WARNING: Symbol version dump /usr/src/linux-headers-2.6.17-10/Module.symve
   rs
              is missing; modules will have no dependencies and modversions.
   
   make -f scripts/Makefile.build obj=/tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz7939/NVI
   DIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL_
   _ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O
   s -fomit-frame-pointer -pipe -mso
   ft-float -mpreferred-stack-boundary=2  -march=athlon -mregparm=3 -ffreestand
   ing -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-point
   er-sign -I/tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv -Wall -W
   implicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wp
   ointer-arith  -Wno-multichar  -Werror -O -fno-common -msoft-float -MD   -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMO
   DULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9631 
   -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGA
   RT_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV
   _PM_MESSAGE_T_PRESENT -DNV_IRQ_HANDLER_WITH_PTREGS_PRESENT -DNV_PCI_CHOOSE_S
   TATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT
   -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)" -c
    -o /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/.tmp_nv.o /tmp
   /selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src
   /nv/nv-linux.h:77,
                    from /tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
   /bin/sh: scripts/genksyms/genksyms: not found
   make[3]: *** [/tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src/nv/nv.o
   ] Error 127
   make[2]: *** [_module_/tmp/selfgz7939/NVIDIA-Linux-x86-1.0-9631-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```


the nvidia module installer (NVIDIA-Linux-x86-1.0-9631-pkg1.run) try to build the kernel module. somebody knows, which packages i need? and what means this in the nvidia log:    /bin/sh: scripts/genksyms/genksyms: not found?

---

### Post by Magni on 2006-12-28
yes, this problem is solved.
if you have you get this error try [this]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")


here comes the next problem :D

when i  use the nvidia driver and i restart /etc/init.d/gdm, the screen is black 
here is my xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 75.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Quadro4 500 GoGL"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Quadro4 500 GoGL"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection


```

---

### Post by Magni on 2006-12-28
It works!!

xorg.conf
```

Section "Device"
    Identifier     "Quadro4 500 GoGL"
    Driver         "nvidia"
    Option	   "NoLogo" "true"
    Option	   "TwinView" "true"
    Option	   "UseDisplayDevice" "DFP"
EndSection

```

---

