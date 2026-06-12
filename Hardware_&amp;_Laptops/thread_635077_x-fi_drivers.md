---
title: "x-fi drivers"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by wallsy on 2007-12-08
I have an X-Fi extreme music I'm trying to install drivers for.

I'm on Ubuntu
I'm using these instructions [http://blackbox.lostwave.net/x-fi/readme.txt](http://blackbox.lostwave.net/x-fi/readme.txt)

Can someone help me with the errors?


./configure
```
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/wallsy/XFiDrv_Linux_US-1.04
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.22-14-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for exported symbol dump_stack... grep: /lib/modules/2.6.22-14-generic/build/kernel/ksyms.c: No such file or directory
no
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for processor type... i586
checking for i386 machine type... default
checking for SMP... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for old kill_fasync... no
checking for dma_addr_t... no
checking for MUTEX macros... no
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for Procfs support... yes
configure: creating ./config.status
config.status: creating Makefile.conf
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# 

```

make
```
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# make
cd /tmp/xfisrc/src/utils/alsaver; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
cd /tmp/xfisrc/src/ossrv; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
rm -rf ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
rm -f ctossrv.ko
cd /tmp/xfisrc/src/emupia; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/emupia'
/tmp/xfisrc/src/emupia/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M emupia_guids.c emupia_main.c   > .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/emupia'
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/emupia'
rm -rf emupia_guids.o emupia_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/emupia'
rm -f emupia.ko
cd /tmp/xfisrc/src/sfman; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/sfman'
/tmp/xfisrc/src/sfman/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M ctsfman_main.c   > .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/sfman'
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/sfman'
rm -rf ctsfman_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/sfman'
rm -f ctsfman.ko
cd /tmp/xfisrc/src/haxfi; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/haxfi'
/tmp/xfisrc/src/haxfi/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M haxfi_main.c   > .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/haxfi'
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/haxfi'
rm -rf haxfi_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/haxfi'
rm -f haxfi.ko
cd /tmp/xfisrc/src/ctalsa; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ctalsa'
/tmp/xfisrc/src/ctalsa/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -DALSA_VERSION_CODE=0 -M amidi.c amixer.c asynth.c ctalsa_main.c dummy.c pcm.c   > .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ctalsa'
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ctalsa'
rm -rf amidi.o amixer.o asynth.o ctalsa_main.o dummy.o pcm.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ctalsa'
rm -f ctalsa.ko
cd /tmp/xfisrc/src/plugins/ct20xut; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
rm -f ct20xut.ko
cd /tmp/xfisrc/src/plugins/ctexfifx; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
rm -rf  *.o *.ko *.o_shipped *~ *.mod.c .*cmd .tmp_versions .depend
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
rm -f ctexfifx.ko
cd /tmp/xfisrc/src/plugins/cthwiut; make clean
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
rm -f cthwiut.ko
cd /tmp/xfisrc/src/utils/alsaver; make
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
gcc -Wall -O  alsaver.c -o alsaver
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
cp -f /tmp/xfisrc/src/utils/alsaver/alsaver .
cd /tmp/xfisrc/src/ossrv; make
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
/tmp/xfisrc/src/ossrv/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -M ctossrv_main.c LinuxReg.c LinuxSys.c osutils.c   > .depend
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
make[1]: Entering directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -c ctossrv_main.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -c LinuxReg.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -c LinuxSys.c
LinuxSys.c: In function ‘sysRegisterInterrupt’:
LinuxSys.c:642: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)
LinuxSys.c:642: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
LinuxSys.c: In function ‘sysGetPagePhysAddr’:
LinuxSys.c:947: warning: passing argument 1 of ‘kvirt_to_phys’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysGetPageBusAddr’:
LinuxSys.c:974: warning: passing argument 1 of ‘kvirt_to_bus’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysWriteFile’:
LinuxSys.c:1626: warning: pointer targets in passing argument 2 of ‘filp->f_op->write’ differ in signedness
LinuxSys.c: In function ‘sysReadFile’:
LinuxSys.c:1675: warning: pointer targets in passing argument 2 of ‘filp->f_op->read’ differ in signedness
LinuxSys.c: At top level:
LinuxSys.c:1463: warning: ‘errno’ defined but not used
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -c osutils.c
osutils.c: In function ‘kvirt_to_page’:
osutils.c:347: warning: passing argument 1 of ‘pmd_offset’ from incompatible pointer type
osutils.c:804:1: warning: "udelay" redefined
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/delay.h:12,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/apic.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/smp.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/smp.h:19,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/desc.h:10,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/elf.h:50,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:15,
                 from osutils.c:20:
/lib/modules/2.6.22-14-generic/build/include/asm/delay.h:20:1: warning: this is the location of the previous definition
osutils.c: In function ‘myDelay’:
osutils.c:814: warning: implicit declaration of function ‘__bad_delay’
osutils.c: At top level:
osutils.c:50: warning: ‘errno’ defined but not used
ld -r ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o -o lin-ctossrv.o
ld -Ur ../../arch/i386/begin.o \
        ../../src/ossrv/lin-ctossrv.o \
        ../../arch/i386/ctossrv.a \
        ../../arch/i386/utils.a \
        ../../arch/i386/end.o -o ctossrv.o_shipped
ld: ../../arch/i386/begin.o: No such file: No such file or directory
make[1]: *** [module] Error 1
make[1]: Leaving directory `/home/wallsy/XFiDrv_Linux_US-1.04/src/ossrv'
make: *** [ctossrv] Error 2
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# 

```

make install
```
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# make install
Copy module files...
cp: cannot stat `ctossrv.ko': No such file or directory
cp: cannot stat `emupia.ko': No such file or directory
cp: cannot stat `ctsfman.ko': No such file or directory
cp: cannot stat `haxfi.ko': No such file or directory
cp: cannot stat `ctalsa.ko': No such file or directory
cp: cannot stat `ct20xut.ko': No such file or directory
cp: cannot stat `ctexfifx.ko': No such file or directory
cp: cannot stat `cthwiut.ko': No such file or directory
make: *** [copy_modules] Error 1
root@wallsy-desktop:/home/wallsy/XFiDrv_Linux_US-1.04# 

```

I'm new but computer knowledgeable.  Please help as I want to listen to my tunes! :)

---

