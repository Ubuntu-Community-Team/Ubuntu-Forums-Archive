---
title: "fglrx fails to build on kernel 3"
date: 2012-03-13
forum: Hardware
---

### Post by sdobz on 2012-03-13
I have tried many things to get this to work. Let's see if the ubuntu community can help.

Using:
[b]Ubuntu 11.10, 64 bit
fglrx, fglrx-updates, amd-driver-installer-12-2-x86.x86_64.run
Lenovo Thinkpad x120e
3.0.0-16-generic[/b]

First I tried installing fglrx-updates on a freshish install of ubuntu, then fglrx, then using a custom ppa (ppa:tista/x120e) then the binary drivers. They all look very similar to any apt-get until they get here:
```
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
Building only for 3.0.0-16-generic
Building for architecture x86_64
Building initial module for 3.0.0-16-generic
ERROR (dkms apport): There was a segmentation fault when trying to build the module
Error! Bad return status for module build on kernel: 3.0.0-16-generic (x86_64)
Consult /var/lib/dkms/fglrx/8.881/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
```

Looking into the make.log:
```
DKMS make.log for fglrx-8.881 for kernel 3.0.0-16-generic (x86_64)
Mon Mar 12 23:23:06 PDT 2012
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.881/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
/usr/src/linux-headers-3.0.0-16-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  CC [M]  /var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.c:1:0: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/cc8O3Bx7.out file, please attach this to your bugreport.
make[2]: *** [/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.881/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

It always looks very similar to this, but with different kernel versions.

The fglrx ati graphical installer halts at "Postprocessing kernel module" 

Here is a thing I tried:
```
sdobz@netbork:/var/lib/dkms/fglrx/8.881/build$ sudo sh make.sh --nohints --uname_r=$(uname -r)
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.881/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
/usr/src/linux-headers-3.0.0-16-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  CC [M]  /var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.c:1:0: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/ccIVY7Uv.out file, please attach this to your bugreport.
make[2]: *** [/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.881/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Any tips?

---

