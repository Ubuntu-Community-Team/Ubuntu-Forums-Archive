---
title: "Ati,: fglrx module and vanilla kernel 2.6.24.x and 2.6.25.x on x86_64"
date: 2008-05-19
forum: Hardware
---

### Post by zeld on 2008-05-19
Hi, yesterday i've done some tests, and i've recompiled kernel on my ubuntu station. I've try vanilla source 2.6.24.4, 2.6.25.x with x=2 and x=5, and the prepatch 2.6.26-rc3, and i ve get some problem with fglrx module install. In fact it wont compile : ), in particular: 

for kernel 2.6.24.x vanilla source, not ubuntu source... i've find this help, but is not completely for x86_64 station, and it work only for x86 : )

allow the kernel to use :

CONFIG_PCI_LEGACY=y

and replace this line on firegl_public.c

dev->spinlock[i] = SPIN_LOCK_UNLOCKED;

with:

spin_lock_init(&dev->spinlock[i]);

The post where is explained:

[http://www.phoronix.com/forums/showthread.php?t=7532&page=1](http://www.phoronix.com/forums/showthread.php?t=7532&page=1)

For kernel 2.6.25.x i've follow this post: 

[http://sarah-a-happy.livejournal.com/90345.html](http://sarah-a-happy.livejournal.com/90345.html)

But anyway with kernel 2.6.24.x, 2.6.25.x with arch x86_64 i've met this problem:

```
/lib/modules/fglrx/build_mod % ./make.sh 
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.24.4/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.24.4'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_put_user_ptr’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1595: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1595: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1595: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1595: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_compat_alloc_user_space’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1914: error: implicit declaration of function ‘compat_alloc_user_space’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1914: warning: return makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_check_pci’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1953: warning: ‘pci_find_slot’ is deprecated (declared at include/linux/pci.h:493)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_pci_find_slot’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2842: warning: ‘pci_find_slot’ is deprecated (declared at include/linux/pci.h:493)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_unregister_ioctl32_conversion’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2974: warning: ‘return’ with a value, in function returning void
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘KAS_SlabCache_Initialize’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:5221: warning: cast from pointer to integer of different size
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.24.4'
make: *** [kmod_build] Error 2
build failed with return value 2

```

and i've found a bug on firegl_public.c.  The problem is here: 

```

/** \brief Get number of available RAM pages
 *  \return Number of available RAM pages
 */
unsigned long ATI_API_CALL KCL_GetAvailableRamPages(void)
{
        struct sysinfo si;
    si_meminfo(&si);
        return si.totalram;
}

#ifdef __x86_64__
void* ATI_API_CALL __ke_compat_alloc_user_space(long size)
{
        return compat_alloc_user_space(size);
}
#endif


```

The function __ke_compat_alloc_user_space return wrong function :\

return compat_alloc_user_space(size);

If you whant compile fglrx with arch x86_64 u must to replace this line :

return compat_alloc_user_space(size);

with this:

return __ke_compat_alloc_user_space(size);


This problem is only found on arch x86_64, and now i live in happiness :"D

:guitar:


P.S.: dont forget in the kernel config to able: 

kernel hacking
[*] Enable __deprecated logic 



Good work guys : )

zeld

_________________

Freedom! 
Freaknet Medialab: [http://www.freaknet.org](http://www.freaknet.org)
Poetry Hacklab: [http://poetry.freaknet.org](http://poetry.freaknet.org)

---

### Post by mcs1 on 2008-09-24
For 2.6.26:

Replace 
```

return compat_alloc_user_space(size);

```

with 

```

return KCL_AMD64_COMPAT32_AllocUserSpace(size);

```

thus it should become:
```

#ifdef __x86_64__
/** \brief Allocate user space for 32-bit app making 64-bit IOCTL
 *  \param size Number of bytes to allocate
 *  \return Pointer to allocated memory
 */
void* ATI_API_CALL KCL_AMD64_COMPAT32_AllocUserSpace(long size)
{
    return KCL_AMD64_COMPAT32_AllocUserSpace(size);
}
#endif


```

Then it compiles and module can be inserted under debian lenny :)
Hope that helps someone
Cheers
MCS

---

### Post by zeld on 2008-10-10
> Then it compiles and module can be inserted under debian lenny
Hope that helps someone
Cheers
MCS

of course!!! i've not try fglrx module with 2.6.26 vanilla source kernel in this time :S(i'm to lazy buuahhauuahua, moreover with this kernel(2.6.26.x) i've some problem with rtc (REAL TIME CLOCK) :S Not work!! and i've not many time to understand where is the problem :S 
However MCS thanks for the post!!! 
I think it  will be useful in the future!!


zeld :-)

---

