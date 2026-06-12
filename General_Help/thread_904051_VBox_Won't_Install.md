---
title: "VBox Won't Install"
date: 2008-08-28
forum: General Help
---

### Post by Unanimated on 2008-08-28
Hi, whenever I try to install VirtualBox through GDebi, the attached picture shows up. I'm running 2.26-19-generic, and it worked flawlessly before I had to format my drive, so I really don't see what the problem is. I have Software Sources set to install the sources for the kernels.

---

### Post by tamoneya on 2008-08-28
can you post the log it is referring to: /var/log/vbox-install.log

---

### Post by Unanimated on 2008-08-28
```
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions ; rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -m32 -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-19-generic/build/include  -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITHOUT_IDT_PATCHING -DUSE_NEW_OS_INTERFACE_FOR_MM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
In file included from /tmp/vbox.2/include/iprt/types.h:72,
                 from /tmp/vbox.2/include/VBox/types.h:21,
                 from /tmp/vbox.2/SUPDRV.h:26,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/types.h:40: error: redefinition of typedef ‘uintptr_t’
/tmp/vbox.2/include/iprt/stdint.h:118: error: previous declaration of ‘uintptr_t’ was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.2/SUPDRV.h:87,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.2/include/VBox/cdefs.h:20,
                 from /tmp/vbox.2/SUPDRV.h:25,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
/tmp/vbox.2/include/iprt/cdefs.h:1042:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vboxdrv] Error 2
```

---

### Post by tamoneya on 2008-08-28
> **Unanimated said:**
> ```
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions ; rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -m32 -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-19-generic/build/include  -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITHOUT_IDT_PATCHING -DUSE_NEW_OS_INTERFACE_FOR_MM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
In file included from /tmp/vbox.2/include/iprt/types.h:72,
                 from /tmp/vbox.2/include/VBox/types.h:21,
                 from /tmp/vbox.2/SUPDRV.h:26,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/types.h:40: error: redefinition of typedef &#8216;uintptr_t&#8217;
/tmp/vbox.2/include/iprt/stdint.h:118: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.2/SUPDRV.h:87,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.2/include/VBox/cdefs.h:20,
                 from /tmp/vbox.2/SUPDRV.h:25,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
/tmp/vbox.2/include/iprt/cdefs.h:1042:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vboxdrv] Error 2
```

Yep here is the issue:```
echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\

```

Try running this:```
cd /usr/src/linux-headers-2.6.24-19-generic
sudo make oldconfig && make prepare
```
Post the results or any errors you get.

---

### Post by Unanimated on 2008-08-28
This is what it said at the end:

```
*** Error during writing of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.

```

---

### Post by Unanimated on 2008-08-28
bump

---

### Post by kerry_s on 2008-08-28
> **Unanimated said:**
> Hi, whenever I try to install VirtualBox through GDebi, the attached picture shows up. I'm running 2.26-19-generic, and it worked flawlessly before I had to format my drive, so I really don't see what the problem is. I have Software Sources set to install the sources for the kernels.

in terminal:
```
sudo su
apt-get install linux-headers-`uname -r` && ln -sf /usr/src/linux-headers-`uname -r` /usr/src/linux
apt-get install libxalan110 libxerces27 build-essential
```

---

### Post by Unanimated on 2008-08-29
Oh, whoops - it turns out I was trying to install the Gutsy version of VBox, when I'm running Hardy. Thanks for the help!

---

