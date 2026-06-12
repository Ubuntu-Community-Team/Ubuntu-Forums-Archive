---
title: "Two libGL.so, Mesa and fglrx, and libgtkglext1-dev depends on libgl1-mesa-dev (ugh)"
date: 2014-06-08
forum: Hardware
---

### Post by doug-coleman on 2014-06-08
Hi,

The Factor language dynamically loads `libGL.so` for its graphical environment. On machines with a Radeon card and the `fglrx-updates` package, the `libGL.so` path is `/usr/lib/fglrx/libGL.so`.

However, if `libgl1-mesa-dev` is installed, there's another `libGL.so` in `/usr/lib/x86_64-linux-gnu/libGL.so`.

Now, I would like to remove `libgl1-mesa-dev`, except that it is required for `libgtkglext1-dev` which contains the function `gtk_gl_init()`, which is required for the graphical environment.

So when running Factor with both drivers installed, the mechanism Factor uses for determining which library to load is to choose the first from the list returned by `ldconfig -p`, which happens to be the Mesa libGL.so, which doesn't work. (I could prefer the `fglrx` version if it exists, but is this the best solution?)

erg@thepower:~/factor$ ldconfig -p | grep libGL.so$
    libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
    libGL.so (libc6,x86-64) => /usr/lib/fglrx/libGL.so

A workaround, if you know all of this, is simply to run it like: `LD_LIBRARY_PATH=/usr/lib/fglrx ./factor`

However, this is not fun to type or create an alias for, and new users to the Factor language who use a Radeon card will not know to do this.

So, is there a way to make `libgtkglext1-dev` not require `libgl1-mesa-dev`? Or, failing that, what's the recommended workaround at the package manager level so that users will not have to go deleting the Mesa `libGL.so` or making aliases to run the Factor binary.

Thanks!
Doug

PS - I'm not sure if there's a similar problem with the proprietary nVidia driver.

---

### Post by doug-coleman on 2014-06-08
Just for kicks, I installed the nvidia drivers, and I guess there would be a similar problem:

erg@thepower:~/factor$ ldconfig -p | grep libGL.so$
	libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
	libGL.so (libc6,x86-64) => /usr/lib/nvidia-304/libGL.so
	libGL.so (libc6) => /usr/lib32/nvidia-304/libGL.so

---

