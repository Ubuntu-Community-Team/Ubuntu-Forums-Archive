---
title: "compiling FTDI driver"
date: 2010-12-09
forum: Hardware
---

### Post by jmnuzi on 2010-12-09
Hi,

I have downloaded the ftdi_sio archive in order
to get a VCP driver for the DLP-IO8 device.

My main present problem is to find missing .h files.
For example, I get
In file included from /lib/modules/2.6.31-22-generic/build/include/linux/kernel.h:11,
                 from ftdi_sio.c:251:
/lib/modules/2.6.31-22-generic/build/include/linux/linkage.h:5:25: error: asm/linkage.h: No such file or directory (Aucun fichier ou dossier de ce type, in French).

Clearly, I have kernel.h and linkage.h
Where is asm/linkage.h?
This looks like an "internal" compilation problem that could
arise in many other circumstances. 

Many thanks in advance.

Jean-Marc Nuzillard
Reims, France

---

### Post by msilva on 2011-03-02
Did you resolved the problem? I Have the same problem. At first I had another

```
atal error: /lib/modules/2.6.35-25-generic-pae/build/include/linux/modversions.h: No such file or directory
```

I corrected it by changing the path to /lib/modules/2.6.35-25-generic-pae/build/include/config/modversions.h

Thanks

---

