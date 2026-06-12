---
title: "Sony Vaio Webcam (Motion Eye)"
date: 2009-09-30
forum: Hardware
---

### Post by razorboy5 on 2009-09-30
Hi

I'm trying to make my friend's motion eye work on his vaio however getting difficulties
i'm following this guide

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

i extracted and got a r5u870 file (not r5u870-0.10.1 but i dont think that it'd matter)
and getting this error

when i try to make
make install


jerom3@jerom3-laptop:~/Desktop/r5u870$ sudo make
make -C /lib/modules/2.6.28-15-generic/build M=/home/jerom3/Desktop/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/jerom3/Desktop/r5u870/r5u870_md.o
In file included from /home/jerom3/Desktop/r5u870/r5u870_md.c:55:
/home/jerom3/Desktop/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/jerom3/Desktop/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/jerom3/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2



it tells u to run it in root all that means is put sudo infront of it rite?
what am i doing wrong :S?

---

