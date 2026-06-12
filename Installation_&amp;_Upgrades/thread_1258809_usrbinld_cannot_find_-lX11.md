---
title: "/usr/bin/ld: cannot find -lX11"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by kcmccorm on 2009-09-05
I am trying to install PGPLOT on my computer, but I keep getting errors.

when I run make this is the output:

cc -c  -I/usr/include -I/usr/local/pgplot -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"2.20\" -DXS_VERSION=\"2.20\" -fPIC "-I/usr/lib/perl/5.10/CORE"   PGPLOT.c
Running Mkbootstrap for PGPLOT ()
chmod 644 PGPLOT.bs
rm -f blib/arch/auto/PGPLOT/PGPLOT.so
cc  -shared -O2 -g -L/usr/local/lib PGPLOT.o  -o blib/arch/auto/PGPLOT/PGPLOT.so     \
       -L/usr/lib -L/usr/local/lib -lpgplot -lcpgplot -lX11 -L/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.1/../../.. -L/usr/lib -lgfortran -lm -L/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.1 -lgcc      \
      
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/PGPLOT/PGPLOT.so] Error 1

It seems it can't find libX11, but I checked and it is installed.  Do I need to create a symbolic link?  If so, I'm linking what to what?

Thank you and sorry for the dumb questions-- I'm a noob.

---

