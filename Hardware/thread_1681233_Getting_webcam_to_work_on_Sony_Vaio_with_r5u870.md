---
title: "Getting webcam to work on Sony Vaio with r5u870"
date: 2011-02-03
forum: Hardware
---

### Post by RingingMaster on 2011-02-03
Had some problems getting webcam to work with downloaded r5u870 module. Hope this helps anyone else with the same errors.

Downloaded the tarball for r5u870 and extracted it.

ringer@vaio:~/Downloads$ tar -xvf r5u870_k2.6.30_i386.tar.bz2

Now to make...

ringer@vaio:~/Downloads/r5u870$ make
make -C /lib/modules/2.6.35-25-generic/build M=/home/ringer/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/ringer/Downloads/r5u870/usbcam/usbcam_util.o
/home/ringer/Downloads/r5u870/usbcam/usbcam_util.c: In function ‘usbcam_urb_allocbuf’:
/home/ringer/Downloads/r5u870/usbcam/usbcam_util.c:163: error: implicit declaration of function ‘usb_buffer_alloc’
/home/ringer/Downloads/r5u870/usbcam/usbcam_util.c:166: warning: assignment makes pointer from integer without a cast
/home/ringer/Downloads/r5u870/usbcam/usbcam_util.c: In function ‘usbcam_urb_freebuf’:
/home/ringer/Downloads/r5u870/usbcam/usbcam_util.c:177: error: implicit declaration of function ‘usb_buffer_free’
make[3]: *** [/home/ringer/Downloads/r5u870/usbcam/usbcam_util.o] Error 1
make[2]: *** [/home/ringer/Downloads/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/ringer/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [all] Error 2

this points to problems starting with usb_buffer_alloc

searching for this gives

[http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en](http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en)

which says usb_buffer_alloc() has been changed in latest kernel to usb_alloc_coherent()

sudo gedit /home/ringer/Downloads/r5u870/usbcam/usbcam_util.c

edit/preferences/ display line numbers

go to line 163 (line number is given in error, above)

change usb_buffer_alloc to usb_alloc_coherent

go to line 177 (line number given in error above)

change usb_buffer_free to usb_free_coherent

try make again - seems to have worked

ringer@vaio:~/Downloads/r5u870$ make
make -C /lib/modules/2.6.35-25-generic/build M=/home/ringer/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/ringer/Downloads/r5u870/usbcam/usbcam_util.o
  LD [M]  /home/ringer/Downloads/r5u870/usbcam/usbcam.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/ringer/Downloads/r5u870/r5u870.mod.o
  LD [M]  /home/ringer/Downloads/r5u870/r5u870.ko
  CC      /home/ringer/Downloads/r5u870/usbcam/usbcam.mod.o
  LD [M]  /home/ringer/Downloads/r5u870/usbcam/usbcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
ringer@vaio:~/Downloads/r5u870$ 

sudo make install   (need sudo)

sudo modprobe r5u870 to manually load the module

and now the webcam works - tested on Skype options / video / test

Looking back at this, the r5u870 file I downloaded was for kernel 2.6.30 and I am currently on 2.6.35, so that was my mistake, trying to use a r5u870 tarball for an older kernel.

---

### Post by itmanvn on 2011-03-11
greatest fix of the day :D

---

