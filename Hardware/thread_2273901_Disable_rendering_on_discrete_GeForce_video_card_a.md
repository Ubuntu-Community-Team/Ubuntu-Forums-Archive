---
title: "Disable rendering on discrete GeForce video card and use it for CUDA only"
date: 2015-04-16
forum: Hardware
---

### Post by sbos on 2015-04-16
Hi! I'm not completely sure if I should post this into Hardware forum, but couldn't a better place for my question. I have a PC with integrated Intel video card and GeForce 980 which I want to use for computations. I've installed Ubuntu 14.10 and nvidia 346 drivers from nvidia repository and everything seems to work properly. However, I'm a bit concerned that there is about 500 megabytes allocated for video memory of GeForce and therefore unavailable for my computational applications. Since I use integrated video card for the output I'd like to prevent somehow GeForce from allocating that memory. I wonder how can do this?

My initial guess was that I should comment out something related to GeForce in my xorg.conf (which seems to be generated automatically by nvidia-xconfig), but the result was either that ubuntu doesn't load (stucks before startig graphics) or my desktop is completely empty. 

What is also quite funny is that I cannot use GeForce for output, the monitor says there is no input signal. I'm actually ok with this as I don't intend to use it for video output.

Can anyone suggest me how to fix this?

---

