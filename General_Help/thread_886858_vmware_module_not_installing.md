---
title: "vmware module not installing"
date: 2008-08-11
forum: General Help
---

### Post by hydratic on 2008-08-11
hello ppl,

I have made the switch from ubuntu 7.10 to 8.04.

All works well of even better .....except vmware server 

using this kernel 
2.6.24-19-generic



This is what happens 

```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

```

I do not have a clue what to look for or how to troubleshoot this.
Can someone help me ?

thanks in advance for any suggestions 

Hydratic

---

