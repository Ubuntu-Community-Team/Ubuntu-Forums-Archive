---
title: "Unable to connect scanner"
date: 2023-03-24
forum: Hardware
---

### Post by satimis on 2023-03-24
Ubuntu 22.04

Scanner : Epson Perfection 3490 Photo

Simple-scan
unable to connect to scanner.  

xsane already installed.

Please advise where to check and fix the problem

Regards

---

### Post by Claus7 on 2023-03-24
Hello,

in some cases xsane is not enough for a scanner to work. Searching a little I found this link:
[https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux](https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux)

where you could find linux drivers for the aforementioned divice.

Regards!

---

### Post by satimis on 2023-03-25
> **Claus7 said:**
> Hello,

in some cases xsane is not enough for a scanner to work. Searching a little I found this link:
[https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux](https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux)

where you could find linux drivers for the aforementioned divice.

Regards!
Hi,

Thanks for your reply and link.

This old scanner worked previously on Ubuntu 20.04 without problem. 

I have the driver of this old scanner in my database
iscan_2.10.0-1.tar.gz

Through difficulties I have installed the driver finally.

Starting Simple-scan it detects Epson scanner.  But clicking "Scan" it popup scanner not found.

It is rather funny to me.

Regards

---

### Post by satimis on 2023-03-28
Hi all,

I tried again install the driver - "iscan_2.10.0-1.tar.gz" on an Ubuntu 22.04VM.  The driver worked seamlessly on Ubuntu 20.04 previously.  On Terminal after extraction.

ls```

ABOUT-NLS     config.h.in    COPYING.LIB  intl           Makefile       po
aclocal.m4    config.log     debian       iscan.spec     Makefile.am    README
AUTHORS       config.rpath   depcomp      iscan.spec.in  Makefile.in    README.ja
backend       config.status  doc          lib            missing        sanei
ChangeLog     config.sub     frontend     libltdl        mkinstalldirs  stamp-h1
compile       configure      include      libtool        NEWS           utils
config.guess  configure.ac   INSTALL      ltmain.sh      NEWS.ja
config.h      COPYING        install-sh   m4             non-free

```

./configure
also went through without complaint.

The problem was on running "make'
make```

.....
......
make[2]: *** [Makefile:353: libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/Iscan/iscan-2.10.0/lib'
make[1]: *** [Makefile:395: all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/Iscan/iscan-2.10.0'
make: *** [Makefile:310: all] Error 2

```

The driver couldn't be installed.

I think that I have to go back to Ubuntu20.04 ???

I'll find a spare SSD for its testing.

Advice and suggestion would be appreciated.

Regards

---

