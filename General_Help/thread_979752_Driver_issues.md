---
title: "Driver issues"
date: 2008-11-12
forum: General Help
---

### Post by Trap3d on 2008-11-12
So i was installing my nvidia 169.04 and no don't tell me to install from hardware installation thing cuz that 1 is not so compatible with wine and for instance doesnt let me play COD4 so im installing this 1 and i get and error saying it cant build nvidia kernel modul thing :ERROR: Unable to build the NVIDIA kernel module.
heres the log:
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Nov 12 15:42:48 2008

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
-> Kernel source path: '/lib/modules/2.6.27-7-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-7-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-7-generi
   c/build SYSOUT=/lib/modules/2.6.27-7-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5385/NVIDIA-Linux-x86-169.04-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  
   -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/in
   clude  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing
   -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mre
   gparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=
   generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fn
   o-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -W
   declaration-after-statement -Wno-pointer-sign -I/tmp/selfgz5385/NVIDIA-Linux
   -x86-169.04-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"169.04\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=
   #s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)
   " -c -o /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/.tmp_nv.o /t
   mp/selfgz5385/NVIDIA-Linux-x86-169
   .04-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   include/asm/bitops.h: In function â&#8364;&#732;set_bitâ&#8364;&#8482;:
   include/asm/bitops.h:60: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arith
   metic
   include/asm/bitops.h: In function â&#8364;&#732;clear_bitâ&#8364;&#8482;:
   include/asm/bitops.h:97: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function â&#8364;&#732;prefetch_rangeâ&#8364;&#8482;:
   include/linux/prefetch.h:57: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/sched.h: In function â&#8364;&#732;object_is_on_stackâ&#8364;&#8482;:
   include/linux/sched.h:1969: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function â&#8364;&#732;sg_virtâ&#8364;&#8482;:
   include/linux/scatterlist.h:199: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used 
   in arithmetic
   In file included from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv-linux.h:107:27: e
   rror: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv-linux.h:109,
                    from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/highmem.h: In function â&#8364;&#732;zero_user_segmentsâ&#8364;&#8482;:
   include/linux/highmem.h:134: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â&#8364;&#732;void *â&#8364;&#8482; used in a
   rithmetic
   In file included from /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v/nv.c:14:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv-linux.h: In funct
   ion â&#8364;&#732;nv_execute_on_all_cpusâ&#8364;&#8482;:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv-linux.h:666: erro
   r: too many arguments to function â&#8364;&#732;on_each_cpuâ&#8364;&#8482;
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c: In function â&#8364;
   &#732;nvos_proc_createâ&#8364;&#8482;:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:605: error: â&#8364;&#732;
   proc_root_driverâ&#8364;&#8482; undeclared (first use in this function)
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:605: error: (Ea
   ch undeclared identifier is reported only once
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:605: error: for
   each function it appears in.)
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c: In function â&#8364;
   &#732;nv_kern_cpu_callbackâ&#8364;&#8482;:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:1270: error: to
   o many arguments to function â&#8364;&#732;smp_call_functionâ&#8364;&#8482;
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:1277: error: to
   o many arguments to function â&#8364;&#732;smp_call_functionâ&#8364;&#8482;
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c: In function â&#8364;
   &#732;nv_kern_vma_nopageâ&#8364;&#8482;:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:1809: error: â&#8364;
   &#732;NOPAGE_SIGBUSâ&#8364;&#8482; undeclared (first use in this function)
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c: At top level:
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:1816: error: un
   known field â&#8364;&#732;nopageâ&#8364;&#8482; specified in initializer
   /tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.c:1816: warning: 
   initialization from incompatible pointer type
   make[3]: *** [/tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/nv/nv.o] 
   Error 1
   make[2]: *** [_module_/tmp/selfgz5385/NVIDIA-Linux-x86-169.04-pkg1/usr/src/n
   v] Error 2
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

---

### Post by Steve1961 on 2008-11-12
Try installing build-essential.  Not that I think this driver will make any difference compared to the one in the repos.

---

### Post by Trap3d on 2008-11-12
umm yea new to linux... whats build essential?

---

### Post by Steve1961 on 2008-11-12
Just type sudo apt-get install build-essential in a terminal.  It will install a basic development environment.

Also, don't forget that wine can do many things but doesn't claim to be able to replicate everything that windows programmes can do when installed in windows.

---

### Post by Trap3d on 2008-11-12
nope no game still the same

---

### Post by Steve1961 on 2008-11-12
Have you given envyNG a try?  I haven't tried it myself as I always stick with the driver versions in the repos - they tend to cause fewer problem,  However, you should bee able to install it from the add/remove menu.  Here's the homepage for info:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Trap3d on 2008-11-13
Im using 8.10 "Interprid Ibex" so envyNG isnt and option for me as it is for 8.04 and earlier and it isnt at add/remove menu so need sumn else...

Lol my bad turns out its compatible so now im trying it....

Nope doesnt work ill search the google bit more

---

