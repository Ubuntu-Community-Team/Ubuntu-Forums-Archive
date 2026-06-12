---
title: "newbie: help needed compiling drivers."
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by sohaibma on 2007-03-03
i am trying to install openchrome drivers for my via vn800 video card in edgy.

from here: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

2d installation goes fine

during 3d installation, every thing goes fine until i come to this section:

**drm kernel modules**

when i enter this:
```
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
```

the following error shows up:
```
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [modules] Error 2

```

i have build essential installed so this error is not related to it.
any idea what's causing this error.

---

### Post by ssavelan on 2007-03-03
You  might try running from the directory in which make is found; running under sudo; or, you may need to ./configure.

---

