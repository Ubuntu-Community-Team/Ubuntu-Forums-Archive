---
title: "Problem installing Webcam ( VGN-SZ / VGP-VCC2 ) in Ubuntu 12.04"
date: 2012-05-04
forum: Hardware
---

### Post by semirx on 2012-05-04
Hi guys
I've got a VGN-SZ17NP and its webcom is VGP-VCC2... Many times I've  tired what Ubuntu folk wrote about the webcams but I've got nothing  yet...

The lsusb says:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bc2:5033 Seagate RSS LLC 
Bus 001 Device 004: ID 054c:0281 Sony Corp. 
Bus 001 Device 006: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 007: ID 05ac:1265 Apple, Inc. iPod Nano 5.Gen
Bus 001 Device 008: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 001 Device 009: ID 05e3:0727 Genesys Logic, Inc. microSD Reader/Writer

```and it seems the webcam have been known by Ubuntu :
```
Bus 001 Device 006: ID 05ca:1830 Ricoh Co., Ltd Visual  Communication Camera VGP-VCC2 [R5U870]
```and I tried these also :

```
sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 
```But, unfortunately the result was nothing...

I've kept receiving this message  :

```
Could not connect to video device (/dev/video0). Please check connection.
```And by this:
```
sudo chmod a+rw /dev/video0
``` I got :
```
chmod: cannot access `/dev/video0': No such file or  directory
```Tried to install old version of r5u87x which supports  these :
```
05ca:1810 HP Pavilion Webcam - UVC
05ca:1830 Sony Visual Communication Camera VGP-VCC2 (for VAIO SZ)
05ca:1832 Sony Visual Communication Camera VGP-VCC3 (for VAIO UX)
05ca:1833 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR1)
05ca:1834 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR2)
05ca:1835 Sony Visual Communication Camera VGP-VCC5 (for VAIO SZ)
05ca:1836 Sony Visual Communication Camera VGP-VCC4 (for VAIO FE)
05ca:1837 Sony Visual Communication Camera VGP-VCC4 (for VAIO FZ)
05ca:1839 Sony Visual Communication Camera VGP-VCC6 (for VAIO CR)
05ca:183a Sony Visual Communication Camera VGP-VCC7 (for VAIO SZ)
05ca:183b Sony Visual Communication Camera VGP-VCC8 (for VAIO FZ)
```Downloaded from here :
```
http://sites.google.com/site/avilella/r5u870-0.10.0.tgz?attredirects=0
```But  by installing this I received these errors :
```
~/Downloads/r5u870-0.10.0$ sudo make
make -C /lib/modules/3.2.0-24-generic/build M=/home/***/Downloads/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /home/***/Downloads/r5u870-0.10.0/r5u870_md.o
In file included from /home/***/Downloads/r5u870-0.10.0/r5u870_md.c:55:0:
/home/***/Downloads/r5u870-0.10.0/usbcam.h:36:29: fatal error: media/video-buf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/***/Downloads/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/***/Downloads/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [all] Error 2
```Anyway, I've got disappointed installing this **** on my laptop...
Any workaround or solution for getting VGP-VCC2 webcam worked on Ubuntu12.04...?

---

