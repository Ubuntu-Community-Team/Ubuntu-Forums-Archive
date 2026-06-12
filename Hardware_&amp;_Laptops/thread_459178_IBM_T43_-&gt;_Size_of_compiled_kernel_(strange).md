---
title: "IBM T43 -&gt; Size of compiled kernel (strange)"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by quetz on 2007-05-30
Hello,

I'm a newbie to kernel compiling staff, but I've red this forum and haven't found the answer.

Feisty Fawn

I wanted to install in in my IBM T43 Active Protection Disk, so I had to recompile the kernel. I followed this instructions:

I patched the kernel and then from /usr/src/linux-source_dir:

# make clean
# make oldconfig
# make-kpkg clean
# make-kpkg --append-to-version=.hdapscustom kernel_image kernel_headers --initrd 

The compilation took 2 hours at least and:
-linux source dir has grown up to 3 Gb
-kernel debian package produced has size of 225 Mb

Well, I think something is wrong. I would be very gratefull If somone could explain me why it is like that, when kernels from repository has got only 70 Mb.

Thank you,
Quetz

---

