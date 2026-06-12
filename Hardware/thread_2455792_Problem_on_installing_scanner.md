---
title: "Problem on installing scanner"
date: 2020-12-28
forum: Hardware
---

### Post by satimis on 2020-12-28
Hi all,

Ubunut 20.04 desktop
Epson Perfection 3490 Photo Scanner

On Epson - Download drivers and Software
[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)
I have download following packages;```

iscan-plugin-gt-f520-1.0.0-1.i386.rpm
iscan-2.10.0-1.i386.rpm
iscan_2.10.0-1.tar.gz 

```

iscan-plugin-gt-f520-1.0.0-1.i386.rpm and iscan-2.10.0-1.i386.rpm are not for Ubuntu20.40

Then I tried to install iscan_2.10.0-1.tar.gz. After extracting it I ran;
$ ./configure (it went throught without problem)
$ make ```

......
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313:23: error: invalid conversion from 'const void*' to 'const dirent**' [-fpermissive]
  313 |   return versionsort (b, a);
      |                       ^
      |                       |
      |                       const void*
In file included from imgstream.hh:45,
                 from imgstream.cc:31:
/usr/include/dirent.h:380:47: note:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
  380 | extern int versionsort (const struct dirent **__e1,
      |                         ~~~~~~~~~~~~~~~~~~~~~~^~~~
imgstream.cc:313:26: error: invalid conversion from 'const void*' to 'const dirent**' [-fpermissive]
  313 |   return versionsort (b, a);
      |                          ^
      |                          |
      |                          const void*
In file included from imgstream.hh:45,
                 from imgstream.cc:31:
/usr/include/dirent.h:381:26: note:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
  381 |    const struct dirent **__e2)
      |    ~~~~~~~~~~~~~~~~~~~~~~^~~~
make[2]: *** [Makefile:353: libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/iscan-2.10.0/lib'
make[1]: *** [Makefile:395: all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/iscan-2.10.0'
make: *** [Makefile:310: all] Error 2

```
I was stopped here.  Please advise how to solve the problem.

Thanks in advance

Regards

---

