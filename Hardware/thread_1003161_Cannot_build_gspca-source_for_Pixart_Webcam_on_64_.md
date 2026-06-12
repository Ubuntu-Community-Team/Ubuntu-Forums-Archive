---
title: "Cannot build gspca-source for Pixart Webcam on 64 bit Intrepid"
date: 2008-12-05
forum: Hardware
---

### Post by kendrick on 2008-12-05
The hardware ID is 093a:2461 which is not on the page of supported webcams at [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) but since every other pixart is supported I assume gspca is what I need. When I try ```
m-a prepare
m-a a-i gspca
``` as suggested I get some errors and stop the build attempt and view the log file:
```
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g ; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##/2.6.27-9.19/g ; s/#KDREV#/2.6.27-9.19/g ; s/_KDREV_/2.6.27-9.19/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-9-generic KERNELDIR=/usr/src/linux-headers-2.6.27-9-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2
```

I see lots of errors and would like some help figuring out what the problem is. Can anyone point me in the right direction?

---

### Post by kendrick on 2008-12-07
Bump

---

### Post by staceyhome on 2009-01-02
Hi,

I've got the same output on both i386 and x64 Ubuntu 8.10 systems. As for missing asm/semaphore.h it's not a big deal, just copy the same file from linux-headers-2.6.27-8 into linux-headers-2.6.27-8-generic directory with the same path. But what about the rest?

Honestly put, I cannot understand how such superior system as linux can take step back and destroy the support for webcamera when switching from 8.04 to 8.10. I expected it to work vice verse.

---

### Post by helmingstay on 2009-02-01
Bump!

---

### Post by relaxedcrazyman on 2009-02-10
i am having the same problem, anyone with any ideas?

---

### Post by cariboo on 2009-02-10
That driver won't build in Intrepid, the author hasn't updates the driver for the newer kernel, If your webcam uses the gspca driver it is now part of the kernel. to check if a driver has been loaded, in a Applications-->Accessories-->Terminal type:

```
lsmod | grep spca
```

the output should look something like this:

[CODElsmod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32][/CODE]

The saa7134 is my TV tuner, but the rest are for the webcam. If the driver is loaded intall xawtv, it is in the repositories, then type:

```
xawtv -c /dev/video0
```

Jim

---

### Post by relaxedcrazyman on 2009-02-10
> **cariboo907 said:**
> That driver won't build in Intrepid, the author hasn't updates the driver for the newer kernel, If your webcam uses the gspca driver it is now part of the kernel. to check if a driver has been loaded, in a Applications-->Accessories-->Terminal type:

```
lsmod | grep spca
```

the output should look something like this:

[CODElsmod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32][/CODE]

The saa7134 is my TV tuner, but the rest are for the webcam. If the driver is loaded intall xawtv, it is in the repositories, then type:

```
xawtv -c /dev/video0
```

Jim



when i type it into terminal nothing happens.

---

### Post by wingnux on 2009-02-18
Same problem here...

---

