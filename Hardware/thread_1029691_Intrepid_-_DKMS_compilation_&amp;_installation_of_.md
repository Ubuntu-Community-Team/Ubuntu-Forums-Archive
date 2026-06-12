---
title: "Intrepid - DKMS compilation &amp; installation of NVIDIA driver 177.80 fails"
date: 2009-01-03
forum: Hardware
---

### Post by AkuTenshi on 2009-01-03
When I installed the restricted driver for my NVIDIA 8600M GT, it failed to compile the DKMS module. On startup, it also says that the DKMS auto-installation fails. The driver still seems to work, as 3D graphics are great and I get 1920x1200 resolution, but the card runs very hot (>80 C idle) and 2d graphics, such as scrolling, bring the system to a dead halt (CPU is Intel T8300, Dual Core 2.4GHz so they can't be the problem). When i try to recompile the DMKS 'nvidia' module i get:
```

$sudo dkms build -m nvidia -v 177.80 --kernelsourcedir /usr/src/linux
Preparing kernel 2.6.27-9-generic for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
Running Generic preparation routine
make mrproper.....
using /usr/src/linux/.config
(I hope this is the correct config for this kernel)
make oldconfig.....
make prepare-all....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-9-generic module KERNDIR=/lib/modules/2.6.27-9-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/usr/src/linux....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-9-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/177.80/build/ for more information.
0
0
```

The log output is:
```

DKMS make.log for nvidia-177.80 for kernel 2.6.27-9-generic (i686)
Sat Jan  3 22:56:41 CET 2009
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1

```

Does anybody know why it cannot compile correctly, or whether the poor 2d performance is simply unrelated to the lack of the DKMS module, in which case is there any other reason it would be so slow? There are also times when parts of the screen do not render properly, such as icons in the system tray being incomplete, or a title-bar colored half selected and half deselected.

---

