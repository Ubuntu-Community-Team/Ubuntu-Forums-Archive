---
title: "Flybook V5 Ubuntu 9.04 I386 ricoh webcam driver r5u87x"
date: 2009-05-03
forum: Hardware
---

### Post by rickyprose on 2009-05-03
Dear friend, I hope someone from the ubuntu worldwide community will hel me because on the italian forum I was not so lucky, because is 2 weeks i'm going mad... with this Ricoh webcam. 

My hardware is a Flybook V5, I installed ubuntu 9.04 and everythings works out of the box, exept the webcam, the fingerprint and touch screen. 

Fingerprint I installed, Touch screen I'm waiting the manufacture is preparing the driver, but what is making me crazy is the webcam I can not understand why is not working, I applied a lot of different guide in internet but the result is still the same.
If someone will help me to have the webcam working I will upload in internet a complete guide how to install ubuntu 9.04 on flybook V5, and I will upload also the driver for the touch screen i'm waiting from the touch screen manufacture.


 Here all my report hope some good technical guy want to reply to me:
 Download the driver from [http://bitbucket.org/ahixon/r5u87x/overview/](http://bitbucket.org/ahixon/r5u87x/overview/) and:
 rickyprose@rickyprose-v5:/Desktop/r5u87x$ make 

cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\”/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\” `pkg-config –cflags glib-2.0 libusb` -c loader.c loader.h cc -g -Wall -o loader loader.o `pkg-config –libs glib-2.0 libusb` rickyprose@rickyprose-v5:/Desktop/r5u87x$ make rules cat contrib/90-r5u87x-loader.rules.in | awk ‘BEGIN{P=1;}/^#BEGINTEMPLATE#/{P=0;} {if (P) print;}’ | grep -v ‘^#’ >contrib/90-r5u87x-loader.rules for sedline in `ls ucode | sed ’s/^r5u87x-\([0-9a-zA-Z]\+\)-\([0-9a-zA-Z]\+\)\.fw$/s\/#VENDORID#\/\1\/g;s\/#PRODUCTID#\/\2\/g/p;d’`; do \ cat contrib/90-r5u87x-loader.rules.in | awk ‘BEGIN{P=0;}/^#BEGINTEMPLATE#/{P=1;}/^#ENDTEMPLATE#/{P=0;} {if (P) print;}’ | grep -v ‘^#’ | sed “$sedline” >>contrib/90-r5u87x-loader.rules; \ done >>contrib/90-r5u87x-loader.rules cat contrib/90-r5u87x-loader.rules.in | awk ‘BEGIN{P=0;}/^#ENDTEMPLATE#/{P=1;} {if (P) print;}’ | grep -v ‘^#’ >>contrib/90-r5u87x-loader.rules rickyprose@rickyprose-v5:/Desktop/r5u87x$ sudo make install install -d /usr install -d /usr/sbin install -m 0755 loader /usr/sbin/r5u87x-loader install -d /usr/lib/r5u87x/ucode install -m 0644 ucode/r5u87x-05ca-1803.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1803.fw install -m 0644 ucode/r5u87x-05ca-1810.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1810.fw install -m 0644 ucode/r5u87x-05ca-1812.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1812.fw install -m 0644 ucode/r5u87x-05ca-1830.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1830.fw install -m 0644 ucode/r5u87x-05ca-1832.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1832.fw install -m 0644 ucode/r5u87x-05ca-1833.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1833.fw install -m 0644 ucode/r5u87x-05ca-1834.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1834.fw install -m 0644 ucode/r5u87x-05ca-1835.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1835.fw install -m 0644 ucode/r5u87x-05ca-1836.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1836.fw install -m 0644 ucode/r5u87x-05ca-1837.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1837.fw install -m 0644 ucode/r5u87x-05ca-1839.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1839.fw install -m 0644 ucode/r5u87x-05ca-183a.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-183a.fw install -m 0644 ucode/r5u87x-05ca-183b.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-183b.fw install -m 0644 ucode/r5u87x-05ca-183e.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-183e.fw install -m 0644 ucode/r5u87x-05ca-1841.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1841.fw install -m 0644 ucode/r5u87x-05ca-1870_1.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1870_1.fw install -m 0644 ucode/r5u87x-05ca-1870.fw /usr/lib/r5u87x/ucode/r5u87x-05ca-1870.fw 

 If we have the rules file generated, install it while we’re here if [ -f contrib/90-r5u87x-loader.rules ]; then \ install -d /etc/udev/rules.d/; \ install -m 0644 contrib/90-r5u87x-loader.rules /etc/udev/rules.d/; \ fi 



rickyprose@rickyprose-v5:/Desktop/r5u87x$ modprobe r5u870 

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release. FATAL: Module r5u870 not found.
 

Anyway I tried: rickyprose@rickyprose-v5:/Desktop/r5u87x$ sudo ./loader [sudo] password for rickyprose: r5u87x firmware loader v0.2
 Searching for device... 

Found camera: 05ca:1803 Warning: Failed to get microcode status.
 Error: Failed to upload firmware to device: Protocol error (code -71).
 

rickyprose@rickyprose-v5:/Desktop/r5u87x$ sudo r5u87x-loader --reload r5u87x firmware loader v0.2
 Searching for device... Found camera: 05ca:1803 

Warning: Failed to get microcode status.
 Error: Failed to upload firmware to device: Cannot send after transport endpoint shutdown (code -108).
 

If you see the webcam is on here the usb list: 

root@rickyprose-v5:/home/rickyprose/Desktop/r5u87x# lsusb 

Bus 001 Device 096: ID 05ca:1803 Ricoh Co., Ltd 
 

But I also noted on the file loader.h this specific line referred to my camera:
 { 0×05CA, 0×1803, 0xFFFF }, * Unknown ucode version.*
 Why when I try to upload the firmware i can not get the microcode status?
 

I tryed a lot of different guide, but no one is helping, someone can write  correct procedure?
 

Thanks a lot. :lolflag:

 

Ciao
 

Riccardo

---

### Post by needhelpplease on 2009-06-08
I have that same cam on my Sony Vaio.  Unfortunately it's a pain to get it working.  In some earlier versions of Ubuntu, someone had put together a very convenient package for that Ricoh driver, which I could install easily.  I just switched to Ubuntu 904 and I can't find that package, but I believe I have compiled it from source, also, and gotten it working nicely.

But it's a lot of hassle.  My advice is to (next time) be aware of this before you buy a notebook with a built-in cam.  And, buy an external cam.  This built-in Ricoh on the Vaio is not good quality.  Any of the good external Logitechs are much better quality, I can use them on any PC I have, and they all "just work".

I guess it would be cool if Medibuntu would package this driver, but probably not that many people need it.

It would be even more cool if Ricoh would sign a binary distribution license for their blobs so this could be in the distribution along with all the other non-free binaries (Flash, many drivers, etc).

---

