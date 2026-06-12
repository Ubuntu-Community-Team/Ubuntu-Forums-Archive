---
title: "drivers logitech qc messenger plus"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by Acgnx on 2009-09-20
I dled drivers from [http://home.mag.cx/messenger/.When](http://home.mag.cx/messenger/.When) i tried to install this happened:
hung@hung-desktop:~/Dokumenty/qc-usb-messenger-1.8$ sudo make install
[sudo] password for hung: 
make -C "/lib/modules/2.6.28-15-generic/build" SUBDIRS="/home/hung/Dokumenty/qc-usb-messenger-1.8" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/hung/Dokumenty/qc-usb-messenger-1.8/.tmp_versions ; rm -f /home/hung/Dokumenty/qc-usb-messenger-1.8/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/hung/Dokumenty/qc-usb-messenger-1.8
  gcc -Wp,-MD,/home/hung/Dokumenty/qc-usb-messenger-1.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)"  -c -o /home/hung/Dokumenty/qc-usb-messenger-1.8/.tmp_qc-driver.o /home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_frame_exit&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:1619: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:1630: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_frame_get&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:1659: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:1666: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_poll&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2625: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_open&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2677: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2688: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2693: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2708: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2714: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2716: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_close&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2742: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2750: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2752: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2767: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2770: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_read&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2791: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2804: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2826: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_mmap&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2848: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2855: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2862: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_v4l_ioctl&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2880: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2884: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:2898: error: &#8216;struct video_device&#8217; has no member named &#8216;type&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3455: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field &#8216;type&#8217; specified in initializer
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_usb_init&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3550: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3556: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3559: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3564: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3665: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3739: error: &#8216;struct video_device&#8217; has no member named &#8216;priv&#8217;
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3772: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3774: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3784: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:3791: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c: In function &#8216;qc_usb_disconnect&#8217;:
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:4060: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:4062: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:4075: error: request for member &#8216;counter&#8217; in something not a structure or union
/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.c:4079: error: request for member &#8216;counter&#8217; in something not a structure or union
make[2]: *** [/home/hung/Dokumenty/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/hung/Dokumenty/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [qcmessenger.ko] Error 2

---

### Post by teramind on 2009-10-07
I have the same problem:

sudo make install                         
[sudo] password for confuzia:                                                          
make -C "/lib/modules/2.6.28-3-rt/build" SUBDIRS="/home/confuzia/Desktop/qc-usb-messenger-1.8" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-3-rt'                                                                           
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \                                                          
        echo;                                                           \                                                                  
        echo "  ERROR: Kernel configuration is invalid.";               \                                                                  
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \                                          
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \                                                  
        echo;                                                           \                                                                  
        /bin/false)                                                                                                                        
mkdir -p /home/confuzia/Desktop/qc-usb-messenger-1.8/.tmp_versions ; rm -f /home/confuzia/Desktop/qc-usb-messenger-1.8/.tmp_versions/*     
make -f scripts/Makefile.build obj=/home/confuzia/Desktop/qc-usb-messenger-1.8                                                             
  gcc -Wp,-MD,/home/confuzia/Desktop/qc-usb-messenger-1.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)"  -c -o /home/confuzia/Desktop/qc-usb-messenger-1.8/.tmp_qc-driver.o /home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c                                                        
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_poll':                                                         
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2625: error: 'struct video_device' has no member named 'priv'                       
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_open':                                                         
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2677: error: 'struct video_device' has no member named 'priv'                       
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_close':
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2742: error: 'struct video_device' has no member named 'priv'
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_read':
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2791: error: 'struct video_device' has no member named 'priv'
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_mmap':
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2848: error: 'struct video_device' has no member named 'priv'
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_ioctl':
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2880: error: 'struct video_device' has no member named 'priv'
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:2898: error: 'struct video_device' has no member named 'type'
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field 'type' specified in initializer
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_usb_init':
/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.c:3739: error: 'struct video_device' has no member named 'priv'
make[2]: *** [/home/confuzia/Desktop/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/confuzia/Desktop/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-3-rt'
make: *** [qcmessenger.ko] Error 2

---

### Post by BitsAndBytes on 2010-01-07
January 7 2009: Ran into the same problem ( Ubuntu 9.10 - the Karmic Koala - released in October 2009 / Kernel version name: 2.6.31-16-generic Kernel source version code: 132639 )

Used the package: qc-usb-messenger-1.8 and set CC to export CC=gcc-4.4 (had the same issue on gcc-3.4 for which many threads point to in creating the quickcam module etc. Found something on uncommenting owner=MODULE_NAME, but this did not solve the issue ( [http://ubuntuforums.org/showthread.php?t=1120710](http://ubuntuforums.org/showthread.php?t=1120710) )

## error section from std-out, from quickcam.sh
mkdir -p /usr/src/qc-usb-messenger-1.8/.tmp_versions ; rm -f /usr/src/qc-usb-messenger-1.8/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/qc-usb-messenger-1.8
gcc -Wp,-MD,/usr/src/qc-usb-messenger-1.8/.qc-driver.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include -Iinclude -I/usr/src/linux-headers-2.6.31-16-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)" -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)" -c -o /usr/src/qc-usb-messenger-1.8/.tmp_qc-driver.o /usr/src/qc-usb-messenger-1.8/qc-driver.c
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_proc_create’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:1127: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/qc-usb-messenger-1.8/qc-driver.c:1140: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_proc_init’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:1182: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/qc-usb-messenger-1.8/qc-driver.c:1188: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_poll’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2625: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_open’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2677: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_close’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2742: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_read’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2791: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_mmap’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2848: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_ioctl’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2880: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-messenger-1.8/qc-driver.c:2898: error: ‘struct video_device’ has no member named ‘type’
/usr/src/qc-usb-messenger-1.8/qc-driver.c: At top level:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field ‘type’ specified in initializer
/usr/src/qc-usb-messenger-1.8/qc-driver.c:3494: warning: initialization from incompatible pointer type
/usr/src/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_usb_init’:
/usr/src/qc-usb-messenger-1.8/qc-driver.c:3739: error: ‘struct video_device’ has no member named ‘priv’
make[2]: *** [/usr/src/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/usr/src/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [qcmessenger.ko] Error 2
ls: cannot access qcmessenger.ko: No such file or directory
[!] Looks like the driver compilation failed.

---

