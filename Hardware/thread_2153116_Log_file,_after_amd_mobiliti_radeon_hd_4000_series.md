---
title: "Log file, after amd mobiliti radeon hd 4000 series drivers install"
date: 2013-06-10
forum: Hardware
---

### Post by Zuppkko on 2013-06-10
I've installed some drivers from amd site (linux 64 version). After installation a pop up said to look into this file for errors. Since i'm  not into computer science i dont know if it is something serious going on. Thanks for any information.

> Check if system has the tools required for installation.
Uninstalling any previously installed drivers.
Unloading radeon module...
ERROR: Module radeon is in use
Unloading drm module...
ERROR: Module drm is in use by radeon,ttm,drm_kms_helper
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.5.0-32-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-32-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘KCL_MEM_AllocLinearAddrInterval’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2152:5: error: implicit declaration of function ‘do_mmap’ [-Werror=implicit-function-declaration]
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2152:13: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-32-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
[Reboot] Kernel Module : update-initramfs

---

### Post by Mark Phelps on 2013-06-10
What version of Ubuntu are you running? If you don't know, open a terminal and enter "uname -r".

---

### Post by clevertomato on 2013-10-01
I see this thread seems to be abandoned, but I'm having the same problem, so I'll try jumping on here before making a new thread. I have been running 10.04 for years on my Dell Studio 1555 with ATI Mobility Radeon 4570. I've always used the proprietary drivers from AMD and they've worked very well for me. I finally installed 12.04.2 (clean install) and tried installing Catalyst 12.4 and also 13.1. Neither work. Supposedly 13.1 legacy is the one that should work, but I get the above problem, same errors when trying to install. I'd run the open source drivers but they keep my notebook fans running on high constantly, which drives me crazy with the noise. It's not acceptable.

I'd appreciate any help.

---

### Post by Yellow Pasque on 2013-10-01
^You need a clean install of 12.04.1 for the legacy driver to work correctly. 12.04.2 uses kernel 3.5, which is a no-no.

---

### Post by clevertomato on 2013-10-01
Thanks, Temüjin. Can you clarify the implications of this? In other words, if I install 12.04.1 and get ATI legacy drivers working, would I have to avoid any future kernel update that comes up in update manager in order to keep the drivers working? It sounds like my video card will keep me from continuing to keep current with Linux.

---

### Post by Yellow Pasque on 2013-10-01
> **shawnboy said:**
> if I install 12.04.1 and get ATI legacy drivers working, would I have to avoid any future kernel update that comes up in update manager in order to keep the drivers working? 
It's okay (and encouraged) to update the kernel, as long as it's version 3.2.x
The same thing goes with Xserver (need to stay in the 1.11.x series).
I don't think update manager installs the "-lts" packages automatically, so you should be okay.


> It sounds like my video card will keep me from continuing to keep current with Linux.
Hopefully, once Ubuntu 13.10 is released, the new dynamic power management code will fix the idle power consumption. (You can even try it now by booting a 13.10 LiveUSB with radeon.dpm=1 in the kernel boot line):
[https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

