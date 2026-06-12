---
title: "[SOLVED] Intrepid and Logitech WebCam"
date: 2008-10-30
forum: Hardware
---

### Post by OnlyWhisky on 2008-10-30
With Intrepid kernel gspca drivers failed to build:
```
/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=gcc-4.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2604: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

```
Does any other driver for Logitech Communicate STX exist?

---

### Post by OnlyWhisky on 2008-10-30
Fixed:
driver is in kernel now. For this camera module is gscpa_zc3xx.

---

### Post by cereal killer on 2008-11-02
Hey, do you mind elaborating a bit please for a n00b. I seem to have the same problem but not sure what the above means.

Thanks.

---

### Post by revanb on 2008-11-03
Hi there,

I have a Logitech E3500 Webcam which worked in Ubuntu Hardy, however now in Intrepid it does not anymore...I tried compiling gspca also, but with the same results: It doesn't compile. I tried loading a few, but not all, os the gspca module that seem to come with Intrepid, but no luck.

Where is there info about which module supports what?

By the way cereal_killer: you can load a module by typing in a terminal:
modprobe module

You can see which modules are loaded with:
lsmod

And remove a module with:
modprobe -r module

You will need to use "sudo" in front of the above commands too.

---

### Post by ffusconi on 2008-12-28
I have the same problem with a Logitech E3500 webcam on Kubuntu 8.10 (the webcam works correctly on Ubuntu 8.04) but I have no idea of how to find gscpa_zc3xx module, I tried to search but with no results.

Thankyou for your help

---

### Post by maxxum on 2008-12-30
It seems that the module gspca_z3xx is installed in my system but the logitech Communicate STX still gives a very bad picture with horizontal lines. It used to work fine in Hardy.
```
:~$ modprobe -l gspca_zc3xx 
/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko
```
Both "modprobe gspca_zc3xx" and "modprobe -v gspca_zc3xx" do not give any output.
Any ideas?

---

### Post by gregflyn on 2008-12-30
Hi I'm running Mint6, Felicia, based on Intrepid. I have the Logitech Quickcam Messenger, and I'm having a really hard time getting it to work in Skype. It works in Mint Control panel (looks a little blue, no pun intended).

I have tried Skype forums and just seaching the web. I have tried installing the new driver qc-usb-messenger-1.8.tar.gz, from the Ubunto Webcam WIKI, but all I get is this:

greg@Boat-puter ~/Desktop/qc-usb-messenger-1.8 $ make
-=- Logitech QuickCam USB camera driver -=-

Makefile target examples:
make all - Compile driver and utilities against current running kernel
make all USER_OPT=-DDEBUG - Compile with debugging code and messages
make all LINUX_DIR=/usr/src/linux - Compile against specified kernel source
make install - Copy driver and utilities into standard locations (needs root)
make install PREFIX=/usr - Copy utilities to /usr/bin instead of /usr/local/bin
make install MODULE_DIR=/lib/modules/2.4.0 - Copy module to /lib/modules/2.4.0/misc
make clean - Remove object files from the source directory

Current configuration:
Driver source directory (PWD):         /home/greg/Desktop/qc-usb-messenger-1.8
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.27-7-generic/build
Module install directory (MODULE_DIR): /lib/modules/2.6.27-7-generic
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):               -DHAVE_UTSRELEASE_H=1
Driver file name (use with insmod):    qcmessenger.ko	
Kernel version code:                   132635
greg@Boat-puter ~/Desktop/qc-usb-messenger-1.8 $ make install
make -C "/lib/modules/2.6.27-7-generic/build" SUBDIRS="/home/greg/Desktop/qc-usb-messenger-1.8" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/greg/Desktop/qc-usb-messenger-1.8/.tmp_versions ; rm -f /home/greg/Desktop/qc-usb-messenger-1.8/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/greg/Desktop/qc-usb-messenger-1.8
  gcc -Wp,-MD,/home/greg/Desktop/qc-usb-messenger-1.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)" -c -o /home/greg/Desktop/qc-usb-messenger-1.8/.tmp_qc-driver.o /home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_frame_exit’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:1619: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:1630: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_frame_get’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:1659: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:1666: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_open’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2688: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2693: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2708: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2714: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2716: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_close’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2750: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2752: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2767: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2770: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_read’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2804: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2826: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_mmap’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2855: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2862: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2884: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:2898: error: ‘struct video_device’ has no member named ‘type’
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3455: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field ‘type’ specified in initializer
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_usb_init’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3550: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3556: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3559: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3564: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3665: error: ‘struct input_dev’ has no member named ‘private’
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3772: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3774: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3784: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:3791: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_usb_disconnect’:
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:4060: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:4062: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:4075: error: request for member ‘counter’ in something not a structure or union
/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.c:4079: error: request for member ‘counter’ in something not a structure or union
make[2]: *** [/home/greg/Desktop/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/greg/Desktop/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [qcmessenger.ko] Error 2

I have tried to get fakevideo to work with gstreamer, but they all need this new driver to run.

Would appreciate any advice, other than the obvious of getting a better cam. I know this is the cheapest one around.

Greg

---

