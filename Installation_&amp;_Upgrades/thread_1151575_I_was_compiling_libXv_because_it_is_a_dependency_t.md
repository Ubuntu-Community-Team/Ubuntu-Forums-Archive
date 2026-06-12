---
title: "I was compiling libXv because it is a dependency to a program which..."
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by 1oooop on 2009-05-07
So, as I was compiling it, I got this error message.

checking for XV... configure: error: Package requirements (x11 xext xextproto videoproto) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XV_CFLAGS and XV_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

I know that I installed it, but I guess the variables aren't right or something. I'm not too sure, I'm kind of a newb at compiling packages. I really don't know how to set variables or where the heck the packages above reside. I'm pretty much a linux newb. I started using ubuntu a few months ago, not enough to really learn the architecture of it.

---

### Post by 1oooop on 2009-05-07
bump?

---

### Post by Partyboi2 on 2009-05-07
> checking for XV... configure: error: Package requirements (x11 xext xextproto videoproto) were not met.this means that you need to install those packages listed but their dev (development) versions.
libxext-dev
libx11-dev
x11proto-video-dev
x11proto-xext-dev

If you require libXv to compile another package you can install it from the Ubuntu repos without having to compile it.
```
sudo apt-get install libxv-dev
```

---

### Post by 1oooop on 2009-05-07
thanks, that totally helps :D

---

