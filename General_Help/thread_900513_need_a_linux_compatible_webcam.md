---
title: "need a linux compatible webcam"
date: 2008-08-25
forum: General Help
---

### Post by sonicb00m on 2008-08-25
Hey Mates!!! :lolflag:

Can anyone recommend me a fairly modern and purchasable webcam for use in Skype on my Ubuntu system?

I have an oldish logitech but I can't get the damn thing to work at all. Will be easier to just buy a new one that people know works without any hassle.

Thank you!:guitar:

---

### Post by Sycron on 2008-08-25
Install cheese an see if it works... :|

```
sudo apt-get install cheese
```

---

### Post by sonicb00m on 2008-08-25
Nah that doesn't work. The camera light isn't even on.

I tried to compile qc-usb from [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) but it doesn't compile.

In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/adam/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/adam/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_i2c_init&#8217;:
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: &#8216;struct urb&#8217; has no member named &#8216;lock&#8217;
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_isoc_start&#8217;:
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/adam/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field &#8216;hardware&#8217; specified in initializer
make[2]: *** [/home/adam/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/adam/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'

---

### Post by sonicb00m on 2008-08-26
Come on , there must be people using webcams. Write em up!

---

### Post by Robin T Cox on 2008-08-27
Here's a list of compatible webcams:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")

And here's how to configure them:
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

---

### Post by Eredeath on 2008-08-27
I bought a logitech webcam skype edition, The only problem i have with it is after a few min of video chat, the image gets dark, haven't quite figured out this problem yet...But otherwise it works well and works out-of-box with Ubunut!

---

### Post by CrusaderAD on 2008-08-27
I have a new logitech that works fine. It was a cheap one so the resolution is crap. But it works.

---

### Post by Crafty Kisses on 2008-08-28
Usually Logitech is the best way to go.

---

### Post by sstusick on 2008-08-28
As the previous poster said...Logitech works well with Ubuntu.

---

### Post by pi.boy.travis on 2008-08-28
Another for Logitech!!

---

