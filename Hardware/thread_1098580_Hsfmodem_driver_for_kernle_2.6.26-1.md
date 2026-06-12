---
title: "Hsfmodem driver for kernle 2.6.26-1 ?"
date: 2009-03-17
forum: Hardware
---

### Post by a.dehqan on 2009-03-17
In The Name Of God

I'll be so thankfull if you guide me ;
Is there any free hsf driver that supports 56 kb/s with kernel 2.6.26 ?

free driver of linuxant.com works but it's receiving speed is limited to 14 B/s
Some of dell drivers has been tested but they can not make module with kernel 2.6.26-1 :

```
(cd /lib/modules/2.6.26-1-686/build && make "CNXT_KERNELSRC=/lib/modules/2.6.26-1-686/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc-4.1" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-1-686'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686'
(cd /lib/modules/2.6.26-1-686/build && make "CNXT_KERNELSRC=/lib/modules/2.6.26-1-686/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc-4.1" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK " clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-1-686'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.26-1-686/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers
(cd /lib/modules/2.6.26-1-686/build && make "CNXT_KERNELSRC=/lib/modules/2.6.26-1-686/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc-4.1" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-1-686'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/lib/hsfmodem/modules/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686'
make: *** [all] Error 2
```

regards dehqan

---

### Post by nixscripter on 2009-03-17
The message says that CFLAGS is being overridden in the Makefile. Open that makefile (/usr/lib/hsfmodem/modules/Makefile), go find the variable CFLAGS, and change it to EXTRA_CFLAGS.

Hope this helps.

---

### Post by Ganton on 2011-03-05
We can find more about it in
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

