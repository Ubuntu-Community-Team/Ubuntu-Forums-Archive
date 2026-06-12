---
title: "Catalyst 9.4 error with kernel 2.6.29.2 + error log."
date: 2009-05-09
forum: Hardware
---

### Post by hanbin973 on 2009-05-09
There was a error while I was installing fglrx.

The error log is 

```
AMD kernel module generator version 2.1
.
Active kernel:
uname -a = Linux hanbin973-desktop 2.6.29-02062902-generic #02062902 SMP Tue Apr 28 16:31:42 UTC 2009 x86_64 GNU/Linux
uname -s = Linux
uname -m = x86_64
uname -r = 2.6.29-02062902-generic
uname -v = #02062902 SMP Tue Apr 28 16:31:42 UTC 2009
.
Target kernel:
uname -a = Linux hanbin973-desktop 2.6.29-02062902-generic #02062902 SMP Tue Apr 28 16:31:42 UTC 2009 x86_64 GNU/Linux
uname -s = Linux
uname -m = x86_64
uname -r = 2.6.29-02062902-generic
uname -v = #02062902 SMP Tue Apr 28 16:31:42 UTC 2009
.
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.29-02062902-generic/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.29-02062902-generic/build/include/linux/autoconf.h says: MODVERSIONS=1
.
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.29-02062902-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.602/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29-02062902-generic'
  CC [M]  /var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.o
In file included from /var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:169:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.h:164:1: warning: "PM_EVENT_SUSPEND" redefined
In file included from /usr/src/linux-headers-2.6.29-02062902-generic/arch/x86/include/asm/apic.h:4,
                 from /usr/src/linux-headers-2.6.29-02062902-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:767,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:91:
include/linux/pm.h:241:1: warning: this is the location of the previous definition
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c: In function ‘KCL_SetPageCache’:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1205: warning: passing argument 1 of ‘set_memory_wb’ makes integer from pointer without a cast
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1209: warning: passing argument 1 of ‘set_memory_uc’ makes integer from pointer without a cast
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c: In function ‘KCL_SetPageCache_Array’:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1223: warning: unused variable ‘ret’
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1222: warning: unused variable ‘i’
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c: In function ‘KCL_GetEffectiveUid’:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1444: error: ‘struct task_struct’ has no member named ‘euid’
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c: In function ‘KCL_PosixSecurityCapSetIPCLock’:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1818: error: ‘struct task_struct’ has no member named ‘cap_effective’
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:1822: error: ‘struct task_struct’ has no member named ‘cap_effective’
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c: In function ‘KCL_MEM_VM_GetRegionPhysAddrStr’:
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:3269: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:3270: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:3271: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.c:3273: warning: return makes pointer from integer without a cast
make[2]: *** [/var/lib/dkms/fglrx/8.602/build/2.6.x/firegl_public.o] error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.602/build/2.6.x] error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29-02062902-generic'
make: *** [kmod_build] error 2
build failed with return value 2
```

Any one knows the problem?

---

### Post by shabazzk on 2009-05-30
Apparently ATi drivers are NOT compatible with kernels newer than 2.6.29 and up. I sent a support request to ATi, to see if they are willing to pinpoint the issue and supply a solution. Until then, guess we'll have to use older kernels.:(

---

