---
title: "Problems with the webcamera agian (ASUS M50Vn)"
date: 2009-04-20
forum: Hardware
---

### Post by dikobrazzius on 2009-04-20
Hi everybody!

I have encountered some problems with my Chicony web cam on ASUS M50Vn laptop. The device's hardware code is 04f2:b106 (CNF7246 (Asus G71V notebooks))

So the problem is, this piece of "equipment" flips the picture upside down. I have read this thread [http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) , patched the uvcvideo driver and failed on loading it... And the old one refuses to work either. Now I don't know what to do.. 



Any help would be appreciated.

---

### Post by tidris on 2009-04-20
If you are using kernel 2.6.26 or newer I think you can bring things back to their original state by reinstalling the kernel. Since the uvc driver is part of kernel 2.6.26 and newer, reinstalling the kernel should reinstall the original uvc driver.

---

### Post by dikobrazzius on 2009-04-21
I've already solved the problem with the uvc driver by downgrading to an older kernel and reinstalling a new one. Yet the problem with the camera still exists.

---

### Post by tidris on 2009-04-21
So if you still want to patch the uvc driver you could try working with the source code from the linuxtv.org repository instead of from berlios. I believe linuxtv.org has newer code than berlios. 

Another option is to install the source code for whatever kernel version you are using now, and modify the driver source files there. That is assuming your kernel version has the uvc driver built in. That seems to me would be the safest approach.

However with either of those approaches you will probably have to edit the source files by hand instead of trying to apply the patch automatically.

---

