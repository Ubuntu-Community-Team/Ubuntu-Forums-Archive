---
title: "Sound Card installation error!"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by usman on 2005-01-25
Hi guys i m trying to install  "Intel high Defiantionn  Audio" driver  in Ubuntu.I give the command ./configure and every thing is good uptill now. but then i try to compile it with "make command" it usually succeedes at all places but then in the end gives me this error message.Every thing upto this message sounds good.here are the messagea!(i have cut short the whole messages cause it would span 8 pages). i hav all kernel header packages installed.Plz help!

[FONT=Arial]

make[1]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /tmp/linux_r30/azx-112504/alsa-driver-1.0.4/kbuild/../acore/hwdep.o
In file included from /tmp/linux_r30/azx-112504/alsa-driver-1.0.4/include/adrive r.h:51,
                 from /tmp/linux_r30/azx-112504/alsa-driver-1.0.4/include/sound/ driver.h:42,
                 from /tmp/linux_r30/azx-112504/alsa-driver-1.0.4/acore/hwdep.c: 22:
include/linux/module.h:309: error: field `refcnt_param' has incomplete type
In file included from /tmp/linux_r30/azx-112504/alsa-driver-1.0.4/acore/hwdep.c: 27:
/tmp/linux_r30/azx-112504/alsa-driver-1.0.4/include/sound/core.h:358:1: warning:  multi-line comment
/tmp/linux_r30/azx-112504/alsa-driver-1.0.4/include/sound/core.h:377:1: warning:  multi-line comment
make[3]: *** [/tmp/linux_r30/azx-112504/alsa-driver-1.0.4/kbuild/../acore/hwdep. o] Error 1
make[2]: *** [/tmp/linux_r30/azx-112504/alsa-driver-1.0.4/kbuild/../acore] Error  2
make[1]: *** [_module_/tmp/linux_r30/azx-112504/alsa-driver-1.0.4/kbuild] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
make: *** [compile] Error 2
[/FONT]

---

