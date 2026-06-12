---
title: "Ubuntu Kernel : Max DVB Adapter"
date: 2016-08-04
forum: Hardware
---

### Post by nioub2e on 2016-08-04
Hello Everyone,

I've made at home a relatively small TVHeadEnd Transcoding server using DVB-T Cards.
The main problem is the kernel which allows me to use only 4 adapters. I've got 12 tuners.
While testing, I am using 16.04 LTS..

So far I've used the following guide to help me set up the kernel : [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
Everything has been compiled, installed all packages (linux-image*.deb and linux-header*.deb), rebooted, selected the right kernel on grub.

After rebooting, typing "uname -a" gives me :
Linux tvheadend-ThinkPad-X201 4.4.0-31-generic #50+DVBMAXADAPTER16 SMP Wed Aug 3 19:30:30 CEST 2016 x86_64 x86_64 x86_64 GNU/Linux

Then I issue "ls /dev/dvb*" I see the same as before : 4 tuners detected but if I issue "lsusb" I can see my 12 USB tuners "PCTV Systems" (model 292e)
I've grabbed the firmware from OpenElec github page which I know it is working since I've used it in the past.

Currently my machine to do these test is a Lenovo X201 Laptop with an i5 and 8GB DDR2-RAM and a 500GB SSD Samsung.
All thoses USB tuner are connected with two differents USB powered hub connected to a outlet wall plug.

If anyone can help me on this problem, appreciate any help
Apologize my english, I am french.

Thanks again,
~Nioub2e

---

