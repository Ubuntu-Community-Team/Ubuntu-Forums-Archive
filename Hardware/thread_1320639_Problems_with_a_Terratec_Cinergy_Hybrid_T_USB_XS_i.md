---
title: "Problems with a Terratec Cinergy Hybrid T USB XS in Ubuntu 9.10 (Karmic Koala)"
date: 2009-11-09
forum: Hardware
---

### Post by zubigwetta on 2009-11-09
I have a Terratec Cinergy Hybrid T USB XS (ID: 0ccd:005e), but I'm unable to use it in Ubuntu 9.10 (Karmic Koala).
The kernel 2.6.31 already includes the em28xx drivers, but there's no firmware installed.
Concerning the firmware, I followed this guide (valid for Ubuntu 9.04 and a tuner with a different ID):
[http://ubuntuforums.org/showthread.php?t=1234777](http://ubuntuforums.org/showthread.php?t=1234777)
but, at the end, Kaffeine or similar softwares were unable to find my DVB tuner...
I tried the same procedure also with Ubuntu 8.04.3 LTS, obtaining the same results.
Any ideas in order to solve this problem?
Thanks in advance.

---

### Post by charliefdom on 2010-03-06
Have you tried to use the drivers provided in the same tutorial you used to install the firmware instead of the ones that shipped with Ubuntu?
You may want to give that a try.

---

### Post by scally on 2010-04-17
i too am having the same issues in 9.10

ive tried installing  the firmware supplied in the tutorial mentioned above but keep getting:

```
sean@sean-desktop:~/em28xx-new$ sudo make

running ./build.sh build

make[1]: Entering directory `/home/sean/em28xx-new'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/sean/em28xx-new/em28xx-video.o
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_config_i2c’:
/home/sean/em28xx-new/em28xx-video.c:411: error: ‘VIDIOC_INT_S_VIDEO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c:411: error: (Each undeclared identifier is reported only once
/home/sean/em28xx-new/em28xx-video.c:411: error: for each function it appears in.)
/home/sean/em28xx-new/em28xx-video.c: In function ‘video_mux’:
/home/sean/em28xx-new/em28xx-video.c:456: error: ‘VIDIOC_INT_S_VIDEO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c:463: error: ‘VIDIOC_INT_I2S_CLOCK_FREQ’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_v4l2_open’:
/home/sean/em28xx-new/em28xx-video.c:734: error: ‘VIDIOC_INT_S_AUDIO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_video_do_ioctl’:
/home/sean/em28xx-new/em28xx-video.c:2462: error: ‘struct device’ has no member named ‘bus_id’
/home/sean/em28xx-new/em28xx-video.c:2879: warning: passing argument 6 of ‘em28xx_do_ioctl’ from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:1922: note: expected ‘v4l2_kioctl’ but argument is of type ‘int (*)(struct file *, unsigned int,  void *)’
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_v4l2_ioctl’:
/home/sean/em28xx-new/em28xx-video.c:2918: warning: passing argument 4 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘int (*)(struct inode *, struct file *, unsigned int,  void *)’
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_init_dev’:
/home/sean/em28xx-new/em28xx-video.c:3214: warning: assignment from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:3301: warning: assignment from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:3340: warning: assignment from incompatible pointer type
make[3]: *** [/home/sean/em28xx-new/em28xx-video.o] Error 1
make[2]: *** [_module_/home/sean/em28xx-new] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/sean/em28xx-new'
sean@sean-desktop:~/em28xx-new$ 
```

any help would be greatly appreciated!

Thanks in advance.

---

