---
title: "cant build module"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by koshari on 2006-11-12
trying to build module for sn9c102-1.32 webcam driver and get this error, 
```
holto@barton:~/downloads/sn9c102-1.32$ make
**************************************************************************
* Building Video4Linux2 driver v1.32 for SN9C10x PC Camera Controllers...*
* Official Linux 2.6.16 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/holto/downloads/sn9c102-1.32 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [modules] Error 2

```

i have installed   ```
kernel-source-2.4.27
``` anything else i need to build this?

---

### Post by koshari on 2006-11-12
ok, i symlinked to the generic build and i think it built the module, 

now how do i install the module??


anyone???

---

