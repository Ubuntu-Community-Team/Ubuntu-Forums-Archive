---
title: "Driver &quot;make&quot; fails, any tips?"
date: 2009-11-02
forum: Hardware
---

### Post by moorsey on 2009-11-02
Hey all,

I think I am trying the right thing, but a few pointers would be helpful.

I have a video capture card for CCTV, but is not supported by Linux, the Windows software that came with it is terrible and I desperately want it to work with Zonealarm.  Although may just return it as not fit for purpose and try and find a Linux compatible card.

I stumbled on a driver for the card though and through it was worth a shot

[http://gitorious.org/tw68/tw68-v2/commits/master]("http://gitorious.org/tw68/tw68-v2/commits/master")

I am cd ing into the folder, downloaded above and then typing "sudo make", but I get a load of errors as follows:

```
root@LUB03:/home/mmoores/Desktop/tw68-tw68-v2# make
make -C /lib/modules/2.6.31-11-generic/build M=/home/mmoores/Desktop/tw68-tw68-v2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-11-generic'
  CC [M]  /home/mmoores/Desktop/tw68-tw68-v2/tw68-core.o
  CC [M]  /home/mmoores/Desktop/tw68-tw68-v2/tw68-cards.o
  CC [M]  /home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.o
/home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.c:145: error: unknown field ‘client_register’ specified in initializer
/home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.c:145: warning: missing braces around initializer
/home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.c:145: warning: (near initialization for ‘tw68_adap_sw_template.dev_released’)
/home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.c:145: warning: initialization makes integer from pointer without a cast
make[2]: *** [/home/mmoores/Desktop/tw68-tw68-v2/tw68-i2c.o] Error 1
make[1]: *** [_module_/home/mmoores/Desktop/tw68-tw68-v2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'
make: *** [all] Error 2
```

If anyone knows how I can fix this, would love to hear from you.  This has been tried on 9.04 and 9.10 with no luck.

Thanks

---

