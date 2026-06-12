---
title: "ATI x700 fglrx64 setup"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by CastorTroy on 2005-09-11
Hi,

I am trying to install the drivers for my video card. I downloaded the linux-headers from synaptic, and I go to dpkg my driver, and it seems to work. However, when I type:"sh make.sh" in the /lib/modules/fglrx/build_mod, I get this error:

make.sh: line 39: gcc: command not found
make.sh: line 45: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
ln: `./libfglrx_ip.a.GCC': File exists
make: *** [libfglrx_ip.a.GCC] Error 1
build failed with return value 2

Does anyone know how I can fix this?

---

### Post by CastorTroy on 2005-09-12
bump...anyone?

---

### Post by mlomker on 2005-09-12
sudo apt-get install build-essential

I spent much of yesterday morning walking a guy through the [entire process.](http://www.ubuntuforums.org/showthread.php?t=64286&highlight=fglrxinfo+mlomker)   You'll find many other threads on the ATI drivers as well, of course.

---

