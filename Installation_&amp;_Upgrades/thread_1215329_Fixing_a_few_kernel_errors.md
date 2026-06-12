---
title: "Fixing a few kernel errors"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by bgbnbigben on 2009-07-17
Hi all,
So, after doing something stupid with --append-to-version whilst building my own kernel, i had to resort to using make instead of the seemingly more-used make-kpkg. However, whilst in the process of makeing, i get the error
```
drivers/char/rocket.c: In function ‘rp_open’:
drivers/char/rocket.c:937: error: ‘ASYNCB_INITIALIZED’ undeclared (first use in this function)
drivers/char/rocket.c:937: error: (Each undeclared identifier is reported only once
drivers/char/rocket.c:937: error: for each function it appears in.)
drivers/char/rocket.c: In function ‘rp_write’:
drivers/char/rocket.c:1644: error: ‘ASYNCB_NORMAL_ACTIVE’ undeclared (first use in this function)
make[2]: *** [drivers/char/rocket.o] Error 1

```

Im assuming that in a header file that im missing, ASYNCB_* hasnt been defined, and hence these macros seem to be failing.
Does anyone know a way to fix this?
Cheers

---

### Post by tommcd on 2009-07-17
This may not be exactly what you are looking for, but you can get newer pre-compiled versions of the Ubuntu kernels from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
If you want to roll your own kernel, here is a tutorial about compiling kernels in Ubuntu:
[http://howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

### Post by bgbnbigben on 2009-07-17
nah, that's not what i wanted - i already had a kernel and had already selected and deselected modules/items that i wanted/didnt want. My question was about fixing that error i got from "make all".
However, what i originally wanted is useless - i realied that i could edit the make-kpkg file, add in the IGNORE_UPPERCASE_VERSION flag and then work from there.
This way, it no longer whinges about the fact that i made a massive debian policy violation :)

Thanks for taking the time out to help

---

### Post by bgbnbigben on 2009-07-17
actually, given that this is the "errors" section, could anyone give me some advice on fixing this lovely error?
```

 create_md5sums_fn           /usr/src/linux-2.6.30.1/debian/linux-image-2.6.30.1.1337
chmod -R og=rX               /usr/src/linux-2.6.30.1/debian/linux-image-2.6.30.1.1337
chown -R root:root           /usr/src/linux-2.6.30.1/debian/linux-image-2.6.30.1.1337
dpkg --build               /usr/src/linux-2.6.30.1/debian/linux-image-2.6.30.1.1337 ..
dpkg-deb: building package `linux-image-2.6.30.1.1337' in `../linux-image-2.6.30.1.1337_2.6.30.1.1337-10.00.Custom_i386.deb'.
dpkg-deb: control directory has bad permissions 2755 (must be >=0755 and <=0775)

```

It's complaining about permissions, but as far as i can tell it's setting it's own permissions.

---

