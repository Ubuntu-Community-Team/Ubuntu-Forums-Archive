---
title: "HFS modem module refusing to compile"
date: 2010-11-24
forum: Hardware
---

### Post by afrodeity on 2010-11-24
The HFSmodem module tries to compile on boot. I am running kernel
2.6.37-020637rc1-generic and have headers installed.

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.37-020637rc1-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.37-020637rc1-generic'
make: *** [all] Error 2

```

---

### Post by IcarusR on 2010-11-24
First I assume you mean HSF modem ?
Is the driver the correct for your architure, 32 or 64 bit ?

Don't know where you got the source tarball from. There is a 32 bit  .deb & tarball or 64 bit tarball on dell site, they are quite old but compiled Ok on my box. Maybe worth a try.

[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/]("http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/")

---

### Post by afrodeity on 2010-11-29
I just get a slightly different message saying no modules found and I need a new kernel. Strange.

---

### Post by afrodeity on 2010-12-03
[http://ubuntuforums.org/showthread.php?t=1597605](http://ubuntuforums.org/showthread.php?t=1597605)

---

### Post by IcarusR on 2010-12-03
Does this mean you have resolved your issue ? I(f so please mark the thread as 'solved' from the 'thread tools' menu. This helps others with similar issue  when searching the forum.
Thanks

---

### Post by afrodeity on 2010-12-04
haven't tested the modem, yet, but I guess it probably is resolved.:)

---

