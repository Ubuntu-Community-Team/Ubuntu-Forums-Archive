---
title: "vx-3000 webcam driver"
date: 2009-02-10
forum: Hardware
---

### Post by aydinozdemir on 2009-02-10
lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 005 Device 003: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000[/COLOR].
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1058:0704 Western Digital Technologies, Inc.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[COLOR="Red"]cd gspcav1-20071224
sudo apt-get install linux-headers-`uname -r` build-essential
sudo ./gspca_build[/COLOR]

ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: "gspca.ko" durumlanamad&#305;: No such file or directory
make: *** [install] Hata 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/aydin/kamera/gspcav1-20071224 CC=cc modules
make[1]:`/usr/src/linux-headers-2.6.27-11-generic' dizinine giriliyor
  CC [M]  /home/aydin/kamera/gspcav1-20071224/gspca_core.o
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/aydin/kamera/gspcav1-20071224/gspca_core.c: In function 'spca5xx_ioctl':
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2463: hata: 'video_usercopy' i&#351;levinin örtük bildirimi
/home/aydin/kamera/gspcav1-20071224/gspca_core.c: Üst düzeyde:
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2609: hata: ilklendiricide bilinmeyen 'owner' alan&#305; belirtilmi&#351;
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2609: UYARI: uyumsuz gösterici türünde ilklendirme
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2611: hata: ilklendiricide bilinmeyen 'type' alan&#305; belirtilmi&#351;
/home/aydin/kamera/gspcav1-20071224/gspca_core.c: In function 'spca50x_create_sysfs':
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2769: hata: 'video_device_create_file' i&#351;levinin örtük bildirimi
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:2780: hata: 'video_device_remove_file' i&#351;levinin örtük bildirimi
/home/aydin/kamera/gspcav1-20071224/gspca_core.c: In function 'spca5xx_probe':
/home/aydin/kamera/gspcav1-20071224/gspca_core.c:4301: hata: atamada uyumsuz türler
[COLOR="Red"]make[2]: *** [/home/aydin/kamera/gspcav1-20071224/gspca_core.o] error 1
make[1]: *** [_module_/home/aydin/kamera/gspcav1-20071224] error 2
make[1]: `/usr/src/linux-headers-2.6.27-11-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [default] error 2[/COLOR]

---

### Post by aydinozdemir on 2009-02-10
I cant install gspca driver for my webcam. I download gspcav1 driver file and make ./configure problem. How can we install webcam driver vx-3000 for ubuntu 8.10. I not professional linux user please advise all details.
thanks.

---

### Post by Joherrer on 2010-05-02
Is there a driver for my VX-3000 webcam?
I'm sorry. I know it is from MS....
I am using Lucid Lynx on my desktop AMD.

---

