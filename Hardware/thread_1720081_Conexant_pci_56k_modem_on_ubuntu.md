---
title: "Conexant pci 56k modem on ubuntu"
date: 2011-04-02
forum: Hardware
---

### Post by Fentanyl on 2011-04-02
I've read this:

[http://ubuntuforums.org/showthread.php?t=1597605&page=1](http://ubuntuforums.org/showthread.php?t=1597605&page=1)

i tried to do the same thing with x64 drivers on ubuntu 11.04 but didn't work.

```

ERROR: Module build failed! Please examine the log file "/etc/hsfmodem/log/buildlog-20110402173304.txt" to determine why.

```

This is the output:



```

driver version 7.68.00.09x86_64oem
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.38-7-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.38-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsInit':
/usr/lib/hsfmodem/modules/osservices.c:1287:80: warning: format '%d' expects type 'int', but argument 2 has type 'long unsigned int'
/usr/lib/hsfmodem/modules/osservices.c:1287:80: warning: format '%d' expects type 'int', but argument 3 has type 'long unsigned int'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
make: *** [all] Error 2

```
I really hope someone can help me :(

---

### Post by IcarusR on 2011-04-03
Did you try the generic tarball as suggested in the linked thread ?

[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06x86_64full/hsfmodem-7.80.02.06x86_64full.tar.gz]("http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06x86_64full/hsfmodem-7.80.02.06x86_64full.tar.gz")

---

### Post by Fentanyl on 2011-04-03
> **IcarusR said:**
> Did you try the generic tarball as suggested in the linked thread ?

[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06x86_64full/hsfmodem-7.80.02.06x86_64full.tar.gz]("http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06x86_64full/hsfmodem-7.80.02.06x86_64full.tar.gz")

Yes, i used exactly that generic tarball :(

---

### Post by Fentanyl on 2011-04-03
I think i know the problem...
Linuxant drivers without all that stuff didn't worked, even limited.. so i think we should wait a new release....

---

### Post by Ganton on 2011-06-13
> **Fentanyl said:**
> I think i know the problem...
Linuxant drivers without all that stuff didn't worked, even limited.. so i think we should wait a new release....
I have been able to use a USB winmodem with a Conexant driver in (K)Ubuntu 11.04, the steps were written in:
[http://ubuntuforums.org/showthread.php?t=1781268](http://ubuntuforums.org/showthread.php?t=1781268)

---

