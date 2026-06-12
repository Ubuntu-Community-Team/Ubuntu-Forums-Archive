---
title: "iHD_drv_video.so error when trying to cast from Chrome"
date: 2021-02-16
forum: Hardware
---

### Post by Alex_Filonov on 2021-02-16
After Feb 1 update Chrome stopped casting to Chromecast from my laptop, which has Intel video. It still was casting from desktop, which has Radeon videocard. After some search, I found out that when initiating cast, Chrome throws the error:  libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed. The same error happens when Chrome is starting, but it's working just fine. I turned hardware acceleration off, casting works.

I thought it's either Chrome itself or Intel drivers. But: I downgraded Chrome to previous version, didn't help. Looked at Feb 1 update, Intel drivers were not updated, neither was libva. The only thing which was updated on Feb 1 and could affect stuff was ubuntu-drivers-common package, but I don't see anything in the package which affects video except, maybe, gpu-manager.

Did anybody have similar experience?

BTW, Firefox works perfect with hardware acceleration.

---

### Post by Alex_Filonov on 2021-03-18
Looks like problem is fixed in Google Chrome beta (90.0.4430.19). Still shows error on the start, but cast is working.
Well, it's good that Google team worked around, but there is still a bug in the Intel video driver libraries.

---

### Post by Alex_Filonov on 2021-04-15
Google fixed the problem in stable 90.0.4430.72 release. There is still problem with Intel video drivers, but for me the problem is resolved.

---

### Post by karolmarki on 2021-04-21
Thank you! It solved my issue too

---

