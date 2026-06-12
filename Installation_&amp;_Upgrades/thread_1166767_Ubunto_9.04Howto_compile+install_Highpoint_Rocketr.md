---
title: "Ubunto 9.04Howto compile+install Highpoint Rocketraid 1810A/1820A open source driver"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by knuterik on 2009-05-22
I used a [previous thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=543872") to find out how to do this on Ubuntu 8.04 and 8.10, but this does not work on ubuntu 9.04.

Seems like the code to be compiled does not support the kernel of 9.04. Has anyone successfully configured their 18X0A raid controller in Ubuntu 9.04?

regards

Knut Erik Ballestad

---

### Post by sburns875 on 2009-07-18
I am experiencing the same problem - followed the instructions on High Point's website and it clearly wants a new driver for 9.04

---

### Post by gunja99 on 2009-12-01
Hi did anyone solve this? I've just upgraded to 9.04 and can't get it working. I don't really wanna have to go back to 8.10 or 8.04, hmmm... I am going to contact Highpoint directly shortly. I have a 1810A, and just can't compile the driver, been trying for 2 days now. he output from the Make command is as follows:

[PHP]make KERNELDIR=/usr/src/linux-source-2.6.28
make -C /usr/src/linux-source-2.6.28 SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.28'
  CC [M]  /home/downloads/highpoint/hpt.o
In file included from /home/downloads/highpoint/hpt.c:310:
/home/downloads/highpoint/gui_lib.c: In function âget_bdevâ:
/home/downloads/highpoint/gui_lib.c:101: error: too many arguments to function âblkdev_getâ
/home/downloads/highpoint/gui_lib.c:105: error: too few arguments to function âblkdev_putâ
/home/downloads/highpoint/gui_lib.c: In function âsd_inuseâ:
/home/downloads/highpoint/gui_lib.c:118: error: too few arguments to function âblkdev_putâ
/home/downloads/highpoint/gui_lib.c: In function âget_sd_nameâ:
/home/downloads/highpoint/gui_lib.c:2630: error: too few arguments to function âblkdev_putâ
make[2]: *** [/home/downloads/highpoint/hpt.o] Error 1
make[1]: *** [_module_/home/downloads/highpoint] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.28'
make: *** [hptmv.ko] Error 2[/PHP]

---

### Post by gunja99 on 2009-12-01
PS: This is what I have sent to Highpoint. I hope they will resolve it, seem to have been good in the past:

> Hi there,
                I have been using the RocketRAID 1810A card with Linux for a couple of years now, and it’s great, but I have recently upgraded to Ubuntu 9.04 and can’t get the driver to compile with the kernel version that is used here. I know the README states that it may not work, but I would really like to upgrade to the latest version of Linux. Is there any plans to fix the source code to work with this kernel, or is driver development no longer going to be done for this range of cards? Please could you let me know, so that I can either downgrade or wait for a fix. I hope that it would be a simple fix in the driver code somewhere. PS, I am not the only person experiencing this problem: [http://ubuntuforums.org/showthread.php?p=8419554#post8419554](http://ubuntuforums.org/showthread.php?p=8419554#post8419554)

Kind regards,
                Martin

---

