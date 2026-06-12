---
title: "Epson rx600 Multi-Photo"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by gasparov on 2005-02-25
Hi,
   I'm trying to install this printer on ubuntu, on linux systems this is usually done by gimp-print-drivers but not this time. Ubuntu recon my printer but there's no relative ppd file, I'm sure that in this version I have there's should be one but not the ubuntu version, no rx500 and no rx600 ppds. I suppose that those file aren't there cause it they were they wouldn't work but wtf!!!
I tried to compile by hand Photo Image Print Systems  ([http://www.epkowa.co.jp/english/linux_e/index.html](http://www.epkowa.co.jp/english/linux_e/index.html)) but cannot make:

```
In file included from pfimg.c:43:
libprtX.h:34:18: ltdl.h: No such file or directory
pfimg.c: In function `mkcode_lib_init':
pfimg.c:348: error: `lt_dlhandle' undeclared (first use in this function)
pfimg.c:348: error: (Each undeclared identifier is reported only once
pfimg.c:348: error: for each function it appears in.)
pfimg.c:348: error: parse error before "lib_handle"
pfimg.c:356: warning: implicit declaration of function `lt_dlinit'
pfimg.c:358: error: `lib_handle' undeclared (first use in this function)
pfimg.c:358: warning: implicit declaration of function `lt_dlopen'
pfimg.c:362: warning: implicit declaration of function `lt_dlerror'
pfimg.c:368: warning: implicit declaration of function `lt_dlsym'
pfimg.c: In function `mkcode_lib_end':
pfimg.c:417: warning: implicit declaration of function `lt_dlclose'
pfimg.c:422: warning: implicit declaration of function `lt_dlexit'
make[2]: *** [pfimg.o] Error 1
make[2]: Leaving directory `/home/gas/.Appz/pips-sprx600_610-2.6.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gas/.Appz/pips-sprx600_610-2.6.2'
make: *** [all-recursive-am] Error 2

```


Any news for this printer coming from "next dog" ? Can I ask what is the reason cause ubuntu has cut off lots of ppd from original gimp drivers differently from Mandrake /Suse??????

---

### Post by MemoryDump on 2005-04-28
has anybody have any luck in getting all the features of the Epson Stylus PHOTO RX500 working? Such as borderless printing for photos using 4x7 photo paper.

Thanks
-MD

---

### Post by MemoryDump on 2005-07-09
*bump* sorry :p

---

