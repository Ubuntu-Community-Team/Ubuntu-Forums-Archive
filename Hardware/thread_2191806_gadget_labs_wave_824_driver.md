---
title: "gadget labs wave 824 driver"
date: 2013-12-04
forum: Hardware
---

### Post by ThomasJefferson on 2013-12-04
so i was just given a wave 824 for free and i'm trying to install the driver in ubuntu studio 12.04.3.
the instructions say to have /usr/src/linux be a symbolic link to the kernel headers.
i've tried:
```
ln -s /lib/mouldes/3.8.0-32-lowlatency/build/include/linux /usr/src/linux
ln -s /usr/src/linux-headers-3.8.0-32-lowlatency/include/linux /usr/src/linux
ln -s /usr/src/linux-lowlatency-3.8-headers-3.8.0-32/include/linux /usr/src/linux
```

and make keeps exiting with an error saying no rule to make target modules.
can someone tell me what i'm doing wrong?

---

### Post by ThomasJefferson on 2013-12-05
Anybody?

---

