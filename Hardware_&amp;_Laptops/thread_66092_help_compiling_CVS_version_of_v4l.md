---
title: "help compiling CVS version of v4l"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by Txukie on 2005-09-16
Hi,
I'm trying to make my TV card AverTV Cardbus E500 work under Ubuntu Hoary with 2.6.10-5-686 kernel. I've found a CVS v4l with the saa7134 drivers that supports it, ive downloaded that CVS from [here](http://dl.bytesex.org/cvs-snapshots/video4linux-20050915-030310.tar.gz) 

I decompress the file under my home directory, and when i do "make" it spits this out
```
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/alberto/video4linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /home/alberto/video4linux/video-buf.o
  CC [M]  /home/alberto/video4linux/v4l1-compat.o
  CC [M]  /home/alberto/video4linux/v4l2-common.o
  CC [M]  /home/alberto/video4linux/btcx-risc.o
  CC [M]  /home/alberto/video4linux/ir-common.o
  CC [M]  /home/alberto/video4linux/bttv-driver.o
  CC [M]  /home/alberto/video4linux/bttv-cards.o
  CC [M]  /home/alberto/video4linux/bttv-risc.o
  CC [M]  /home/alberto/video4linux/bttv-if.o
In file included from /home/alberto/video4linux/bttv-if.c:35:
/home/alberto/video4linux/bttvp.h:55:28: media/tveeprom.h: No such file or directory
fixdep: /home/alberto/video4linux/.bttv-if.o.d is empty
  CC [M]  /home/alberto/video4linux/bttv-vbi.o
  CC [M]  /home/alberto/video4linux/bttv-i2c.o
  CC [M]  /home/alberto/video4linux/bttv-gpio.o
In file included from /home/alberto/video4linux/bttv-gpio.c:36:
/home/alberto/video4linux/bttvp.h:55:28: media/tveeprom.h: No such file or directory
fixdep: /home/alberto/video4linux/.bttv-gpio.o.d is empty
  CC [M]  /home/alberto/video4linux/cx88-video.o
In file included from /home/alberto/video4linux/cx88.h:33,
                 from /home/alberto/video4linux/cx88-video.c:37:
/home/alberto/video4linux/media/video-buf-dvb.h:2:20: dvbdev.h: No such file or directory
/home/alberto/video4linux/media/video-buf-dvb.h:3:20: dmxdev.h: No such file or directory
/home/alberto/video4linux/media/video-buf-dvb.h:4:23: dvb_demux.h: No such file or directory
/home/alberto/video4linux/media/video-buf-dvb.h:5:21: dvb_net.h: No such file or directory
/home/alberto/video4linux/media/video-buf-dvb.h:6:26: dvb_frontend.h: No such file or directory
In file included from /home/alberto/video4linux/cx88.h:33,
                 from /home/alberto/video4linux/cx88-video.c:37:
/home/alberto/video4linux/media/video-buf-dvb.h:25: error: field `demux' has incomplete type
/home/alberto/video4linux/media/video-buf-dvb.h:26: error: field `dmxdev' has incomplete type
/home/alberto/video4linux/media/video-buf-dvb.h:27: error: field `fe_hw' has incomplete type
/home/alberto/video4linux/media/video-buf-dvb.h:28: error: field `fe_mem' has incomplete type
/home/alberto/video4linux/media/video-buf-dvb.h:29: error: field `net' has incomplete type
make[2]: *** [/home/alberto/video4linux/cx88-video.o] Error 1
make[1]: *** [_module_/home/alberto/video4linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make: *** [default] Error 2
``` 

Don't know why because the files actually exist but under a soft link.
I've read the README file of my chip it says

Build
=====

Pick up videodev + v4l2 patches from [http://bytesex.org/patches/](http://bytesex.org/patches/).
Configure, build, install + boot the new kernel. You'll need at least
these config options:

CONFIG_I2C=m
CONFIG_VIDEO_DEV=m

Type "make" to build the driver now. "make install" installs the
driver. "modprobe saa7134" should load it. Depending on the card you
might have to pass card=<nr> as insmod option, check CARDLIST for
valid choices.

Those options mean i need to recompile my kernel? OR am i ok with my Ubuntu precompiled? How the hell do i apply those patches? I've visited the site and it has .biff.gz files which i don't know how to use.
Please somebody help as i'm really looking forward to watch TV on my great Linux box. Thanks!

---

