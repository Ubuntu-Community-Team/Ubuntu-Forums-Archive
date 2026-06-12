---
title: "Cisco 3000 vpn installation error"
date: 2008-09-23
forum: General Help
---

### Post by miork on 2008-09-23
So I'm attempting to install the Cisco vpn software my work uses, which has worked before for me on other distributions, and usually has been a plug and chug with their install script, which just asks your options and compiles the program.  

However, when I try to do it on this new Ubuntu 8.04.1 build, I get the following errors : 

```
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /root/vpnclient/linuxcniapi.o
In file included from /root/vpnclient/Cniapi.h:15,
                 from /root/vpnclient/linuxcniapi.c:31:
/root/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/root/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/root/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```

It seems that both include/linux/types.h and GenDefs.h in the Cisco software use uintptr_t as a type... unfortunately ubuntu uses it as an unsigned long and Cisco uses it as an uint32 or uint64, depending on your system.  Removing Cisco's typedef causes an error, and I'm not sure if I want to go messing around with the system includes.  

Is there another option?  I really want to keep this machine as ubuntu, but I need that vpn client, and i may have to use a different distribution if this is unfixable.

thanks!

---

### Post by miork on 2008-09-24
Bump and an update ...

Word is that this software package only really works with older versions of the kernel.  2.6.24 is right out, 2.6.22 probably will work fine.  I've never done a kernel reinstall without wiping out the current OS and starting from scratch with a different version, is there an easy way to do this or should I just find an older version of Ubuntu to work with?

thanks :)

---

