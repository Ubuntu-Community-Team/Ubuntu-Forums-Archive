---
title: "[SOLVED] fglrx with Mobility Radeon on Hardy"
date: 2008-06-28
forum: Hardware
---

### Post by meronh on 2008-06-28
I upgraded to Hardy a few weeks ago and haven't had 3D acceleration working since then (I have a Mobility Radeon X1300).  I've already installed the latest fglrx drivers using Envy, but I have the following error in my Xorg.0.log:

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

I've attached the whole file, in case that helps.  Thanks in advance for assistance.

---

### Post by pytheas22 on 2008-06-28
You may want to try using [envy]("http://www.albertomilone.com/nvidia_scripts1.html").  In my experience, it's a great way to get a video card configured with minimal headache.  If envy doesn't work, we can trouble-shoot your error messages, but there's a good chance that envy will fix everything on its own.

---

### Post by reacocard on 2008-06-28
> **pytheas22 said:**
> You may want to try using [envy]("http://www.albertomilone.com/nvidia_scripts1.html").  In my experience, it's a great way to get a video card configured with minimal headache.  If envy doesn't work, we can trouble-shoot your error messages, but there's a good chance that envy will fix everything on its own.

read his post: he already tried envy

---

### Post by meronh on 2008-06-28
Yes, I already tried reinstalling the drivers with Envy to no effect.

---

### Post by pytheas22 on 2008-06-28
> Yes, I already tried reinstalling the drivers with Envy to no effect.

Sorry, I read too quickly.

What is the output of:

```
modprobe -vf fglrx
```

---

### Post by meronh on 2008-06-28
I get:
install /sbin/lrm-video fglrx

---

### Post by pytheas22 on 2008-06-28
> I get:
install /sbin/lrm-video fglrx

Try opening /etc/modprobe.d/lrm-video and comment-out the line that says "install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS"  Then reboot.  Does it work?

If not, did you try an apt-get remove --purge of fglrx and a reinstall?

---

### Post by meronh on 2008-06-28
That did it, thanks so much!

---

### Post by pytheas22 on 2008-06-28
> That did it, thanks so much!

I can't really take the credit; I just got it from this [post]("http://ubuntuforums.org/showpost.php?p=4910317&postcount=319").  But I'm glad it worked.  And sorry again for carelessly reading your post the first time.

---

