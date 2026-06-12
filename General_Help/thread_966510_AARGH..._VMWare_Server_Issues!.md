---
title: "AARGH... VMWare Server Issues!"
date: 2008-11-01
forum: General Help
---

### Post by shaunfink on 2008-11-01
Hey all!

I'm fairly new to the Linux OS.. When I started playing around with it i started off with Mandriva, then to Fedora and now i'm using Ubuntu. Currently I have 8.10 installed and i'm having an issue with VMWARE Server!

The installation works all fine and well but once i run vmware-config.pl I get to a stage where i'm building the vmmon module. This is where I get errors. Here's the output that i get:

> 
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



Any ideas as to what the problem is and how I can fix this?

Cheers

---

### Post by starclouded on 2008-11-29
Hi, this solved my problem>

wget -c [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

tar -xzvf  vmware-update-2.6.27-5.5.7-2.tar.gz && cd vmware-update-2.6.27-5.5.7-2 && sudo perl runme.pl

enjoy sorry for my english [http://ubuntuforums.org/images/icons/icon11.gif](http://ubuntuforums.org/images/icons/icon11.gif)

---

### Post by zabaksmers17 on 2008-12-18
Thanks, this solved my problem also!

---

### Post by scott.nightingale on 2009-05-17
brilliant, thank you!

---

