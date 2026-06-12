---
title: "[SOLVED] how to install the kernel headers"
date: 2008-09-14
forum: General Help
---

### Post by nice007 on 2008-09-14
> my display card ATI 3850 can't work fine in the Ubuntu 7.10 Gusty with kernel 2.6.22-15,so I updated it to Ubuntu8.04 in order to make a better support.But unfortunately,after that it installed  a new kernel 2.6.24-15,and the new kernel can't work even to start system.So I have to start the system with the old one (2.6.22.15)

Then I tried to install the display card driver using ati-driver-installer-8-8-x86.x86_64.run and followed the instruction from the forum.
After " [QUOTE]ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/hardy"
 I got 5 deb files and I tried to instll them with "> sudo dpkg -i *.deb"(onlyl these deb files in the folder)
and got a error mes:

(Reading database ... 109663 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 2:8.522-0ubuntu1 (using fglrx-amdcccle_8.522-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 2:8.522-0ubuntu1 (using fglrx-kernel-source_8.522-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-modaliases 2:8.522-0ubuntu1 (using fglrx-modaliases_8.522-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Preparing to replace xorg-driver-fglrx 2:8.522-0ubuntu1 (using xorg-driver-fglrx_8.522-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 2:8.522-0ubuntu1 (using xorg-driver-fglrx-dev_8.522-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (2:8.522-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error! Your kernel source for kernel 2.6.22-15-generic cannot be found at
/lib/modules/2.6.22-15-generic/build or /lib/modules/2.6.22-15-generic/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.22-15-generic (i686) first.
Done.

Setting up fglrx-modaliases (2:8.522-0ubuntu1) ...
Setting up xorg-driver-fglrx (2:8.522-0ubuntu1) ...

Setting up xorg-driver-fglrx-dev (2:8.522-0ubuntu1) ...
Setting up fglrx-amdcccle (2:8.522-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

[/QUOTE]
it seems that I don't have the linux headers of kernel 2.6.22-15-generi,but I don't konw how to download and install them.
I tried to use the > "sudo apt-get install  linux-headers-2.6.22-9 linux-headers-2.6.22-9-generic"
and it give me the following ms:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.22-15 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-15 has no installation candidate

I don't konw what to do now,I have puzzled about the problems for 3 days ,any ideal are appreciated ,thanks

---

### Post by nice007 on 2008-09-15
solve it by myself,close this post

---

### Post by indulis on 2008-10-09
You are supposed to tell other people how you solved the problem!  So it helps others who hit the same problem.  Thanks!

---

