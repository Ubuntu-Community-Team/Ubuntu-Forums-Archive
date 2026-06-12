---
title: "Toshutils compiling problem"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by test02 on 2007-01-29
Hi people!

I have the following problem compiling Toshutils:

error: X11/xpm.h: no such file or directory
/usr/include/asm-i386/io.h:4:26: error: linux/string.h: no such file or directory

Any clues of what I'm missing here?

I have these files in the usr/include folder, but the 'make depend' command can't find them...

---

### Post by lvanderree on 2007-01-29
why not run

```
sudo apt-get install toshutils
```

works fine for me on my M200

---

### Post by n1m4 on 2007-04-08
the header files are in the "xpm-dev" so
==> apt-get install libxpm-dev

Nima Moghadam

---

