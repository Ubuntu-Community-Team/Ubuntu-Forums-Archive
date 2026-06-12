---
title: "Highpoint 7280 driver?"
date: 2016-01-15
forum: Hardware
---

### Post by Benjiro on 2016-01-15
Has anybody got the Highpoint 7280 ( the r750's smaller brother ) driver to work on recent kernels?

So far my attempts at compiling the driver has been running into several issues.

[SIZE=-1]It seems that the drivers on the website are only limited to      kernel 2.6. They never released any update beyond the 1.0 version. 

Tried forcing the driver to      assume its compiling for 2.6 fails because of changes in the recent kernels.
      
      Example: "in expansion of macro ‘HPT_KMAP_TYPE’   *pbuf =      kmap_atomic(HPT_SG_PAGE(sg), HPT_KMAP_TYPE) + sg->offset;"
"[/SIZE]osm_linux.h:178:23: note: each undeclared identifier is reported only once for each function it appears in #define HPT_KMAP_TYPE KM_BIO_SRC_IRQ"...

---

### Post by Benjiro on 2016-01-16
Contacted Highpoint and after several attempts got a updated driver ( 1.1 ) that official supported the 3.10 kernel. But also runs perfectly on newer 3.x kernels.

Just make, install and ...

I attached it so it can be of help for anybody else running into this problem.

---

