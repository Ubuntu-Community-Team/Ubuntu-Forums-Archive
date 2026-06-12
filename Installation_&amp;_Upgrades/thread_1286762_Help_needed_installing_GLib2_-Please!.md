---
title: "Help needed installing GLib2 -Please!"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by baskar007 on 2009-10-09
hi friends,
I am using Ubuntu 9.04
I want to install Glib 2.21 for  audacious 2.1.

I downloaded Glib tar.Gz file. When i try to compile i got a error on Make command. Here is the report

> mv -f .deps/gthread-impl.Tpo .deps/gthread-impl.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall  -version-info 2102:0:2102 -export-dynamic    -o libgthread-2.0.la -rpath /usr/local/lib gthread-impl.lo  -lpthread -lrt ../glib/libglib-2.0.la 
libtool: link: gcc -shared  .libs/gthread-impl.o   -Wl,-rpath -Wl,/media/Baskar/ALL -Wl,-rpath -Wl,about -Wl,-rpath -Wl,Ubuntu/backup -Wl,-rpath -Wl,Package/glib-2.21.2/glib/.libs -lpthread -lrt ../glib/.libs/libglib-2.0.so    -Wl,-soname -Wl,libgthread-2.0.so.0 -o .libs/libgthread-2.0.so.0.2102.0
libtool: link: (cd ".libs" && rm -f "libgthread-2.0.so.0" && ln -s "libgthread-2.0.so.0.2102.0" "libgthread-2.0.so.0")
libtool: link: (cd ".libs" && rm -f "libgthread-2.0.so" && ln -s "libgthread-2.0.so.0.2102.0" "libgthread-2.0.so")
/bin/sed: can't read Package/glib-2.21.2/glib/libglib-2.0.la: No such file or directory
libtool: link: `Package/glib-2.21.2/glib/libglib-2.0.la' is not a valid libtool archive
make[2]: *** [libgthread-2.0.la] Error 1
make[2]: Leaving directory `/media/Baskar/ALL about Ubuntu/backup Package/glib-2.21.2/gthread'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/Baskar/ALL about Ubuntu/backup Package/glib-2.21.2'
make: *** [all] Error 2


Please help me friends?

---

