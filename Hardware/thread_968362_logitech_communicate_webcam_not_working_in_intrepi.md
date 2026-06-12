---
title: "logitech communicate webcam not working in intrepid"
date: 2008-11-02
forum: Hardware
---

### Post by alejaaandro on 2008-11-02
hi guys...

i upgraded to intrepid yesterday.. overall, i didn't have any problems, except that my webcam won't work anymore..

i used easycam2 to install the driver (that's what i had used in hardy too).. this is what i get..

```

GO !
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/usr/share/EasyCam2/drivers/quickcam/testquickcam'
rm testquickcam -f
make[1]: Leaving directory `/usr/share/EasyCam2/drivers/quickcam/testquickcam'
make -C "/lib/modules/2.6.27-7-generic/build" SUBDIRS="/usr/share/EasyCam2/drivers/quickcam" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/share/EasyCam2/drivers/quickcam/.tmp_versions ; rm -f /usr/share/EasyCam2/drivers/quickcam/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/share/EasyCam2/drivers/quickcam
  gcc -Wp,-MD,/usr/share/EasyCam2/drivers/quickcam/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)" -c -o /usr/share/EasyCam2/drivers/quickcam/.tmp_qc-driver.o /usr/share/EasyCam2/drivers/quickcam/qc-driver.c
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_frame_exit’:ig.h': File exists

/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:1619: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:1630: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_frame_get’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:1659: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:1666: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_v4l_open’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2688: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2693: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2708: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2714: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2716: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_v4l_close’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2750: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2752: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2767: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2770: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_v4l_read’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2804: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2826: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_v4l_mmap’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2855: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2862: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_v4l_ioctl’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2884: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:2898: error: ‘struct video_device’ has no member named ‘type’
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3455: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: At top level:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3487: error: unknown field ‘type’ specified in initializer
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_usb_init’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3550: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3556: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3559: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3564: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3665: error: ‘struct input_dev’ has no member named ‘private’
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3772: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3774: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3784: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:3791: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c: In function ‘qc_usb_disconnect’:
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:4060: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:4062: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:4075: error: request for member ‘counter’ in something not a structure or union
/usr/share/EasyCam2/drivers/quickcam/qc-driver.c:4079: error: request for member ‘counter’ in something not a structure or union
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: *** [/usr/share/EasyCam2/drivers/quickcam/qc-driver.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/quickcam] Error 2
make: *** [qcmessenger.ko] Error 2
FATAL: Module qcmessenger not found.
qcset: can not open /dev/video0 (No such file or directory)


```

this is my webcam

```

lsusb
Bus 003 Device 002: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate


```

any ideas?

if you need any more info, just ask..

---

### Post by csseurg6 on 2008-11-04
[https://bugs.launchpad.net/ubuntu/+bug/293176](https://bugs.launchpad.net/ubuntu/+bug/293176) :)

---

