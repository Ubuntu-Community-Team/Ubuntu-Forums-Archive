---
title: "TouchScreen driver issues"
date: 2009-05-07
forum: Hardware
---

### Post by audub on 2009-05-07
I am trying to install drivers to configure an Aspen touch screen on ubuntu 9. I am quite new to this, but according to the readme-file, this should be peace of cake. Well - it is not ;)

The drivers come with a setup-file that is supposed to do most of the work for me. But, when running the setup-file, I get the following errors: 

```
audub@doffen:/home/audub/kernel2.6/TouchUtilityPackage$ sudo ./setup
make -C /lib/modules/2.6.24-23-server/build SUBDIRS=/home/audub/kernel2.6/TouchUtilityPackage modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-server'
  CC [M]  /home/audub/kernel2.6/TouchUtilityPackage/touch.o
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:728: warning: initialization from incompatible pointer type
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:746: error: unknown field &#8216;mode&#8217; specified in initializer
/home/audub/kernel2.6/TouchUtilityPackage/touch.c: In function &#8216;idealtek_probe&#8217;:
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:772: error: &#8216;SLAB_ATOMIC&#8217; undeclared (first use in this function)
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:772: error: (Each undeclared identifier is reported only once
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:772: error: for each function it appears in.)
/home/audub/kernel2.6/TouchUtilityPackage/touch.c: At top level:
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:848: error: unknown field &#8216;owner&#8217; specified in initializer
/home/audub/kernel2.6/TouchUtilityPackage/touch.c:848: warning: initialization from incompatible pointer type
make[2]: *** [/home/audub/kernel2.6/TouchUtilityPackage/touch.o] Error 1
make[1]: *** [_module_/home/audub/kernel2.6/TouchUtilityPackage] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-server'
make: *** [default] Error 2
```

Can anyone please help me locate the problem? I appreciate all help :)

---

