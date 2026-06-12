---
title: "NVIdia.."
date: 2008-10-30
forum: Hardware
---

### Post by leetone on 2008-10-30
Ubuntu 8.10, Fresh Install today.
Geforce 2 MX

Setting up nvidia-96-kernel-source (96.43.05-0ubuntu10) ...
nvidia-96-kernel-source: Configuring nvidia-96-kernel-source

nvidia-96-kernel-source: Configuring nvidia-96-kernel-source

Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 96.43.05
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/96.43.05/build/ for more information.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (i686) first.
Done.

nvidia-96-kernel-source: Installed nvidia-96-kernel-source

Setting up nvidia-glx-96 (96.43.05-0ubuntu10) ...
nvidia-glx-96: Configuring nvidia-glx-96

nvidia-glx-96: Configuring nvidia-glx-96


nvidia-glx-96: Installed nvidia-glx-96

Here is end of make.log:

/var/lib/dkms/nvidia/96.43.05/build/nv.c: In function &#8216;__nv_setup_pat_entries&#8217;:
/var/lib/dkms/nvidia/96.43.05/build/nv.c:833: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/96.43.05/build/nv.c: In function &#8216;__nv_restore_pat_entries&#8217;:
/var/lib/dkms/nvidia/96.43.05/build/nv.c:859: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/96.43.05/build/nv.c: In function &#8216;nv_kern_cpu_callback&#8217;:
/var/lib/dkms/nvidia/96.43.05/build/nv.c:1170: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/96.43.05/build/nv.c:1173: error: too many arguments to function &#8216;smp_call_function&#8217;
/var/lib/dkms/nvidia/96.43.05/build/nv.c:1177: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/96.43.05/build/nv.c:1180: error: too many arguments to function &#8216;smp_call_function&#8217;
/var/lib/dkms/nvidia/96.43.05/build/nv.c: In function &#8216;nv_kern_vma_nopage&#8217;:
/var/lib/dkms/nvidia/96.43.05/build/nv.c:1699: warning: return makes pointer from integer without a cast
make[3]: *** [/var/lib/dkms/nvidia/96.43.05/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/96.43.05/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2

I also tried installing driver from nvidia.com, but its fail. can't build nvidia kerel module :/

linux-headers and build-essential are installed

---

### Post by X10D3 on 2008-10-30
It looks as if nVidia or ubuntu has blocked the use of nvidia drivers in this version. I am going to uninstall unbuntu and not look back. I have a notebook with an nvidia card. Ubuntu doesn't work for me anymore.

---

### Post by solitaire on 2008-10-30
Their is an issue with the 96.43.05 Binaries! they are not compatible with the latest version of Xorg.
Nvidia have release beta drivers 96.43.09 yesterday.

See here to download the Binaries:
[http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

---

### Post by Luggy on 2008-11-02
I'm glad that they got these binaries out so soon. Sure enough my video card wasn't supported ( GeForce 4200 Ti ) with the new release but by installing these binaries after the fact got it working.

I hope the Ubuntu Team can fix it so all new fresh installs can have their old video cards supported in the future.

---

### Post by solitaire on 2008-11-03
Their is updated files just waiting to be made into .deb's, tested and then uploaded to the repositories.
Hopefully it will be ready before the next US President is named... ;) lol!!

But don't worry! fix is nearly there!! :D

See this bug thread:
[https://bugs.launchpad.net/bugs/251107](https://bugs.launchpad.net/bugs/251107)

---

