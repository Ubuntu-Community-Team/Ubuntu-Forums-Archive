---
title: "TW68-v2 drrivers installation error"
date: 2012-03-20
forum: Hardware
---

### Post by ebros on 2012-03-20
I have installed before tW68-v2 drivers to Ubuntu and Kubuntu 11.10 by bocking the rows 970 and 1000 in tw68-core.c (ir-remote) and it works. Now I have tried to do the same way in xubuntu 11.10, but i shall get compilation error as:
root@eeropc:~/tw68-v2# make
make -C /lib/modules/3.0.0-16-generic/build M=/root/tw68-v2 modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-3.0.0-16-generic"
  CC [M]  /root/tw68-v2/tw68-core.o
In file included from /root/tw68-v2/tw68-core.c:43:0:
/root/tw68-v2/tw68.h:50:31: vakava virhe (serious fault): media/ir-common.h: Tiedostoa tai hakemistoa ei ole( File or index dont exist)
compilation terminated.
make[2]: *** [/root/tw68-v2/tw68-core.o] Error 1
make[1]: *** [_module_/root/tw68-v2] Error 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-3.0.0-16-generic"
make: *** [all] Error 2
Something has changed in tw68-core.c or something is missing in xubutu 11.10, but what?
Does somebody know, how can I success to install tw68-v2 drivers?

---

### Post by ebros on 2012-03-23
I have solved  my problem myself. I have bocked rows 986 and 1018 in tw68-v2/tw68-core.c and tw68-v2/tw68.h  row 50 depending on ir-remote, which I have not in my dvb-card. After that make and make install succeed.

---

