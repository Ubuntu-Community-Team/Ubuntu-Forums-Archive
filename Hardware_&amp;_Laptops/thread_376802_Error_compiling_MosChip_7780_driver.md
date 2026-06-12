---
title: "Error compiling MosChip 7780 driver"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by kiaton on 2007-03-05
I'm trying to compile official driver for my IRDA dongle - MosChip 7780 ([http://www.moschip.com/data/products/MCS7780/Linux_7780.tar.gz]("http://www.moschip.com/data/products/MCS7780/Linux_7780.tar.gz")), but with no success.

```
me@edgy:~/Linux_7780$ make
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/andrey/Desktop/Linux_7780 modules;
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /home/andrey/Desktop/Linux_7780/mcs7780.o
/home/me/Linux_7780/mcs7780.c:81: error: expected ‘)’ before string constant
/home/me/Linux_7780/mcs7780.c:145: error: unknown field ‘owner’ specified in initializer
/home/me/Linux_7780/mcs7780.c:145: warning: initialization from incompatible pointer type
/home/me/Linux_7780/mcs7780.c: In function ‘mcs7780_disconnect’:
/home/me/Linux_7780/mcs7780.c:355: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/home/me/Linux_7780/mcs7780.c:355: error: (Each undeclared identifier is reported only once
/home/me/Linux_7780/mcs7780.c:355: error: for each function it appears in.)
/home/me/Linux_7780/mcs7780.c: In function ‘mcs7780_rx_submit’:
/home/me/Linux_7780/mcs7780.c:1104: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/home/me/Linux_7780/mcs7780.c: In function ‘mcs7780_tx_submit’:
/home/me/Linux_7780/mcs7780.c:1280: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
make[2]: *** [/home/me/Linux_7780/mcs7780.o] Error 1
make[1]: *** [_module_/home/me/Linux_7780] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-386'
make: *** [default] Error 2
```

How knows how to compile mcs7780 driver for Edgy?

---

