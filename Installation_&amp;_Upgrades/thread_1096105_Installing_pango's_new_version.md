---
title: "Installing pango's new version"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by alejachipia on 2009-03-14
Hi everybody,

I got a problem I've been installing glib-2.18.4 and pango-1.8.6. glib is located in a folder that I created. But pango cannot find the address. This is the error that I got when I try to compile:

root@bebe:/home/alejachipia/pango-1.20.5# make
make  all-recursive
make[1]: Entering directory `/home/alejachipia/pango-1.20.5'
Making all in pango
make[2]: Entering directory `/home/alejachipia/pango-1.20.5/pango'
make  all-recursive
make[3]: Entering directory `/home/alejachipia/pango-1.20.5/pango'
Making all in mini-fribidi
make[4]: Entering directory `/home/alejachipia/pango-1.20.5/pango/mini-fribidi'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/alejachipia/pango-1.20.5/pango/mini-fribidi'
make[4]: Entering directory `/home/alejachipia/pango-1.20.5/pango'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall   -o pango-querymodules querymodules.o libpangox-1.0.la    libpango-1.0.la /usr/opt/glib-2.18.4/ 
gcc -g -O2 -Wall -o .libs/pango-querymodules querymodules.o /usr/opt/glib-2.18.4/  ./.libs/libpangox-1.0.so /home/alejachipia/pango-1.20.5/pango/.libs/libpango-1.0.so -lX11 ./.libs/libpango-1.0.so -lm  -Wl,--rpath -Wl,/usr/opt/pango-1.20.5//lib
/usr/bin/ld: /usr/opt/glib-2.18.4/: No such file: File format not recognized
collect2: ld returned 1 exit status
make[4]: *** [pango-querymodules] Error 1
make[4]: Leaving directory `/home/alejachipia/pango-1.20.5/pango'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/alejachipia/pango-1.20.5/pango'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/alejachipia/pango-1.20.5/pango'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alejachipia/pango-1.20.5'
make: *** [all] Error 2

Can somebody help me please? :(

---

