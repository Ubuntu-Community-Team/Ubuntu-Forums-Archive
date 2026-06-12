---
title: "driver for usb-hardlock"
date: 2008-05-20
forum: Hardware
---

### Post by cmmozos on 2008-05-20
i,

I am trying to install a USB-hardlock from Aladdin for local use on ubuntu 8.04. The first step is to compile the driver running a script, but I receive the next error:

cm@cm-laptop:~/aksparlnx-1.6-x86$ sudo sh ./build.sh --install
make -C /lib/modules/2.6.24-16-generic/build here=$(pwd)/ SUBDIRS=$(pwd) modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/cm/aksparlnx-1.6-x86/Makefile". Fix it to use EXTRA_CFLAGS. Alto.
make[1]: *** [_module_/home/cm/aksparlnx-1.6-x86] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [kernel26] Error 2
aksparlnx.ko does not exist!
aborting
cm@cm-laptop:~/aksparlnx-1.6-x86$

it seems to be a problem with the kernel during the compilation of the driver, but I am a new user of linux and I dont know to fix the problem.

driver and script: [ftp://ftp.aladdin.com/pub/aladdin.de....7-i386.tar.gz](ftp://ftp.aladdin.com/pub/aladdin.de....7-i386.tar.gz)


please, can anybody help me?!!!

thanks.

C.M.

---

### Post by iceflame on 2010-01-30
hello

i am encountering the same problem.
did you get to solve it in any way?

greets

---

