---
title: "Updating Parblo Coat 22/Monoprice 22 Drivers"
date: 2018-07-28
forum: Hardware
---

### Post by MZ250Supa5 on 2018-07-28
I bought on of these excellent pen monitors some 18 months ago, and initially it was a bit of a treasure hunt to find drivers for it, I succeeded as the drivers for my pen monitor model, Parblo Coast 22 are the same that someone has developed for the similar Monoprice pen monitor. Thus driver has always needed to be re-installed when there is a kernel update and sometimes a 'roll back' to using a previous driver has been required as the driver hasn't yet been adapted for use with the new kernel, but usually that has only meant a few days wait until that occurs, and the driver can be reinstalled using the latest kernels. However, this seems to no longer be happening, and do fat the maintainer, who took over responsibility for the driver in September 2017 has not responded to e-mails, or messages left on his github page: 

[https://github.com/odysseywestra/Monoprice_22_linux_kernel_module](https://github.com/odysseywestra/Monoprice_22_linux_kernel_module)

Leaving me with a pen monitor I can't use on Ubuntu Mate.

When I try to compile the driver, this is the output I am getting:

```
padi@branwen:~$ cd Monoprice_22_linux_kernel_module-master/
padi@branwen:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/4.15.0-29-generic/build M=/home/padi/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
  CC [M]  /home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o
In file included from ./include/linux/jiffies.h:7:0,
                 from /home/padi/Monoprice_22_linux_kernel_module-master/mono_22.c:34:
./include/linux/kernel.h:6:20: fatal error: stdarg.h: No such file or directory
compilation terminated.
scripts/Makefile.build:339: recipe for target '/home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o' failed
make[2]: *** [/home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o] Error 1
Makefile:1552: recipe for target '_module_/home/padi/Monoprice_22_linux_kernel_module-master' failed
make[1]: *** [_module_/home/padi/Monoprice_22_linux_kernel_module-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:10: recipe for target 'all' failed
make: *** [all] Error 2
padi@branwen:~/Monoprice_22_linux_kernel_module-master$ 

```

If anyone has any idea how I can overcome the issue of not being able to install this driver I'd be delighted to see a reply. It's a shame that the initial discussion on the github page about including support fro this pen monitor in the kernel has not (yet) borne fruit.

---

