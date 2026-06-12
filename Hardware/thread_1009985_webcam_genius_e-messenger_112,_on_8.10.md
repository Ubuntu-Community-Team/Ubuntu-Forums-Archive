---
title: "webcam genius e-messenger 112, on 8.10"
date: 2008-12-13
forum: Hardware
---

### Post by bunker6 on 2008-12-13
Hello everyone.

*Suddenly* I've become a proud owner of a brand new web camera. The point is pretty obvious, however, it doesn't work.

It's a "Genius e-Messenger 112", identifying in **lsusb** as
```
Bus 002 Device 003: ID 093a:2476 Pixart Imaging, Inc.
```
when plugged in, which produces a dramatic
```
b6:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
```
I've seen guys getting it to work successfully for older kernels by recompiling GSPCA with some patches.

I'm on a 8.10 with a 2.6.27-9-generic kernel and the rest is pretty much intact.

Any help is greatly appreciated.

---

### Post by bunker6 on 2008-12-14
Thanks for no one replying, I'm still playing with my mighty webcam.

Installing a fresh build of libv4l-0 from [http://linuxtv.org/hg/v4l-dvb/summary](http://linuxtv.org/hg/v4l-dvb/summary) did a part of the trick, after some kicking I have vido even in Skype.

Now I want to turn it upside down and make a little more bright.

---

### Post by merwizard on 2009-01-05
I've also had the chance to play with this webcam. I have both Linux Mint 6 (Ubuntu 8.10 based) and Mandriva 2009.0. I've only tested it on Mandriva where I was able to find a dkms snapshot of the v4l-dvb in their repositories, dating from December 6 2008.

The image is also upside down and quite overexposed in daylight, with wrong contrast. I am not able to use the webcam with Skype, even if I set  "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" before starting Skype. I am able to capture images only using the Cheese application.

So, for the moment, everyone should avoid this webcam.

---

### Post by maickel on 2010-11-21
thank you for your informaion, and there is alot informaion in [e-messenger]("http://www.ajaxlines.com/ajax/stuff/article/emessenger.php")

---

