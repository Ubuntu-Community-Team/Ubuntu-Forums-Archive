---
title: "WebCam Sony Vaio vgn-fz470e not working"
date: 2009-09-25
forum: Hardware
---

### Post by alexandrevaz on 2009-09-25
Hey guys, i've been reading a lot of solution about installing vaio webcam but didn solve my problems.

My Vaio is fz470e and my webcam model is:

Bus 005 Device 002: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 044e:3012 Alps Electric Co., Ltd 
Bus 007 Device 003: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Someone have any idea how can i install it? Well i'll be waiting your help!

Well i'm kinda noob about linux/ubuntu so if you give me details about that will help a lot! thank you:guitar:

---

### Post by alexandrevaz on 2009-09-25
I tried to follow this website intruction [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) but look what hapened when i writte make and sudo make intall:

make:
```
alexandre@alexandre-laptop:~/r5u870$ make
make -C /lib/modules/2.6.28-15-generic/build M=/home/alexandre/r5u870 V=0 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/alexandre/r5u870/usbcam/usbcam_dev.o
In file included from /home/alexandre/r5u870/usbcam/usbcam_dev.c:21:
/home/alexandre/r5u870/usbcam/usbcam_priv.h:123: error: field ‘um_v4l_fops’ has incomplete type
/home/alexandre/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_work_ref’:
/home/alexandre/r5u870/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
make[3]: ** [/home/alexandre/r5u870/usbcam/usbcam_dev.o] Erro 1
make[2]: ** [/home/alexandre/r5u870/usbcam] Erro 2
make[1]: ** [_module_/home/alexandre/r5u870] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.28-15-generic'
make: ** [all] Erro 2

```sudo make install:
```
alexandre@alexandre-laptop:~/r5u870$ sudo make install
make -C /lib/modules/2.6.28-15-generic/build M=/home/alexandre/r5u870 V=0 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/alexandre/r5u870/usbcam/usbcam_dev.o
In file included from /home/alexandre/r5u870/usbcam/usbcam_dev.c:21:
/home/alexandre/r5u870/usbcam/usbcam_priv.h:123: error: field ‘um_v4l_fops’ has incomplete type
/home/alexandre/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_work_ref’:
/home/alexandre/r5u870/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
make[3]: ** [/home/alexandre/r5u870/usbcam/usbcam_dev.o] Erro 1
make[2]: ** [/home/alexandre/r5u870/usbcam] Erro 2
make[1]: ** [_module_/home/alexandre/r5u870] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.28-15-generic'
make: ** [all] Erro 2

```Do you know why those errors??

---

