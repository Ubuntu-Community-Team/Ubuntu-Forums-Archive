---
title: "Ubuntu 8.10 and Genius Look 110 Webcam"
date: 2009-02-22
forum: Hardware
---

### Post by Dobroslav on 2009-02-22
Well, I've downloaded zr364xx driver and in terminal I typed make and I got this:

```
   Building zr364xx driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/dobri/Desktop/zr364xx-0.71/zr364xx.o
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c: In function ‘zoran_mmap’:
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:812: error: implicit declaration of function ‘vm_insert_page’
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:812: error: implicit declaration of function ‘vmalloc_to_page’
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c: At top level:
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:837: error: unknown field ‘owner’ specified in initializer
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:837: warning: initialization from incompatible pointer type
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:839: error: unknown field ‘type’ specified in initializer
/home/dobri/Desktop/zr364xx-0.71/zr364xx.c:840: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/dobri/Desktop/zr364xx-0.71/zr364xx.o] Error 1
make[1]: *** [_module_/home/dobri/Desktop/zr364xx-0.71] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

```

What I need to do?

---

