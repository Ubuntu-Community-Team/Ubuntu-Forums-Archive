---
title: "Broadcom Crystal HD: trbl installing drivers on 11.04"
date: 2011-04-30
forum: Hardware
---

### Post by LavianoTS386 on 2011-04-30
I am trying to install the drivers for the Broadcom Crystal HD decoder card in my Asus EeePC. I'm following [these]("http://forum.xbmc.org/showthread.php?t=66650&page=3") instructions, which worked in 10.10, but aren't working now. 

Here's what I get when I try to make

> ~/crystalhd/driver/linux$ make
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/anthony/crystalhd/driver/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/anthony/crystalhd/driver/linux/crystalhd_lnx.o
/home/anthony/crystalhd/driver/linux/crystalhd_lnx.c:362:2: error: unknown field ‘ioctl’ specified in initializer
cc1: warnings being treated as errors
/home/anthony/crystalhd/driver/linux/crystalhd_lnx.c:362:2: error: initialization from incompatible pointer type
make[2]: *** [/home/anthony/crystalhd/driver/linux/crystalhd_lnx.o] Error 1
make[1]: *** [_module_/home/anthony/crystalhd/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2


Can anyone help me?

---

### Post by freewindster on 2011-05-05
For Natty use the latest source from: [http://git.wilsonet.com/crystalhd.git/](http://git.wilsonet.com/crystalhd.git/)

The install instructions from the original "Broadcom" release will work.

---

### Post by GT-OS on 2011-10-19
I have the same error and i compiled it for latest git but i have the same error also i  got it work on debian 6 by changing  the the Makefile path to '/usr/src/linux-headers-2.6.32-5-686' rather than '/lib/modules/$(KVER)/build' and it worked.
I did the same thing in ubuntu 11.10 its not working.

---

### Post by freewindster on 2011-10-19
> **GT-OS said:**
> I have the same error and i compiled it for latest git but i have the same error also i  got it work on debian 6 by changing  the the Makefile path to '/usr/src/linux-headers-2.6.32-5-686' rather than '/lib/modules/$(KVER)/build' and it worked.
I did the same thing in ubuntu 11.10 its not working.
Fix compile in Onieric

Edit file: driver/linux/crystalhd_flea_ddr.c
Add the following to the top of the file near the "includes" 

#include <linux/delay.h>

---

### Post by Issssy on 2011-10-19
Confirmed. I had to do that, and the

#include <stdint.h>

fix in libcrystalhd_if.h noted [here]("http://forum.xbmc.org/showthread.php?t=62708&page=50"). (post 498 ) to get the driver up and running on my HP Mini 110 with 11.10 --  confirmed working with XBMC.

b

---

### Post by LavianoTS386 on 2011-11-15
^ That worked great thank you so much!

---

### Post by lawois on 2011-11-29
> **Issssy said:**
> Confirmed. I had to do that, and the

#include <stdint.h>

fix in libcrystalhd_if.h noted [here]("http://forum.xbmc.org/showthread.php?t=62708&page=50"). (post 498 ) to get the driver up and running on my HP Mini 110 with 11.10 --  confirmed working with XBMC.

b


Hi,

I am a noobie to ubuntu and linux in general, and I have to say that I have spent numerous hours online searching for answers in getting my crystalhd card to work on my HP mini 110, which is running Ubuntu 11.10.  Since you mention that you got it to work on your HP mini, would you be able to help me out in getting mine to work?  I have followed instructions from the readme file on Broadcom's package, but it didnt work.  I am now trying to find a way to restart from the beginning and maybe posting error codes I get whenever I do make and make install?

Any one else that could help?

Thanks!

edit:

This is what I get when I do make:

root@andre-HP-Mini-110-1000:/home/andre/crystalhd/driver/linux# make
make -C /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/andre/crystalhd/driver/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/andre/crystalhd/driver/linux/crystalhd_lnx.o
/home/andre/crystalhd/driver/linux/crystalhd_lnx.c:360:2: error: unknown field &#8216;ioctl&#8217; specified in initializer
/home/andre/crystalhd/driver/linux/crystalhd_lnx.c:360:2: error: initialization from incompatible pointer type [-Werror]
/home/andre/crystalhd/driver/linux/crystalhd_lnx.c:360:2: error: (near initialization for &#8216;chd_dec_fops.llseek&#8217;) [-Werror]
cc1: all warnings being treated as errors

make[2]: *** [/home/andre/crystalhd/driver/linux/crystalhd_lnx.o] Error 1
make[1]: *** [_module_/home/andre/crystalhd/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2

---

