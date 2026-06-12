---
title: "problems"
date: 2005-11-10
forum: General Help
---

### Post by spyke01 on 2005-11-10
ok, i have a microsoft fingerprint reader, which has to have xp and ie 4.0+ installed, well ive installed wine, and am now trying to install ies4linux, but that needs cabextract, so i got cabextract, but it need a c compiler in $PATH so i tried finding a c compiler in the add programs app but nothing there, i also tried searching it for gcc but couldnt find it, any ideas?

EDIT: i ran sudo apt-get install gcc, and that worked, but i now get this error:
checking for C compiler default output file name... configure error: C compiler cannot create executable

---

### Post by RAOF on 2005-11-10
You need to get the "build-essential" package, and possibly the autotools packages:
```
sudo apt-get install build-essential libtool
```

---

### Post by spyke01 on 2005-11-11
after i ran the install for those, i ran
./configure
make && make install

i get this in konsole:

> 
make  all-am
make[1]: Entering directory `/tmp/cabextract-1.1'
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o system.o `test -f 'mspack/system.c' || echo './'`mspack/system.c
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o cabd.o `test -f 'mspack/cabd.c' || echo './'`mspack/cabd.c
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o lzxd.o `test -f 'mspack/lzxd.c' || echo './'`mspack/lzxd.c
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o mszipd.o `test -f 'mspack/mszipd.c' || echo './'`mspack/mszipd.c
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o qtmd.o `test -f 'mspack/qtmd.c' || echo './'`mspack/qtmd.c
rm -f libmspack.a
ar cru libmspack.a system.o cabd.o lzxd.o mszipd.o qtmd.o
ranlib libmspack.a
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o cabextract.o `test -f 'src/cabextract.c' || echo './'`src/cabextract.c
src/cabextract.c: In function &#8216;create_output_name&#8217;:
src/cabextract.c:758: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217;
 differ in signedness
gcc  -g -O2   -o cabextract  cabextract.o libmspack.a
gcc -DHAVE_CONFIG_H -I. -I. -I.  -I./mspack -DMSPACK_NO_DEFAULT_SYSTEM   -g -O2
-c -o cabinfo.o `test -f 'src/cabinfo.c' || echo './'`src/cabinfo.c
src/cabinfo.c: In function &#8216;convertUTF&#8217;:
src/cabinfo.c:249: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c: In function &#8216;getinfo&#8217;:
src/cabinfo.c:355: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:357: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:361: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:363: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:369: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:371: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:375: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:377: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:446: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
src/cabinfo.c:447: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; di
ffer in signedness
gcc  -g -O2   -o src/cabinfo  cabinfo.o
make[1]: Leaving directory `/tmp/cabextract-1.1'
make[1]: Entering directory `/tmp/cabextract-1.1'
test -z "/usr/local/bin" || mkdir -p -- . "/usr/local/bin"
  /usr/bin/install -c 'cabextract' '/usr/local/bin/cabextract'
/usr/bin/install: cannot create regular file `/usr/local/bin/cabextract': Permis                                            sion denied
make[1]: *** [install-binPROGRAMS] Error 1
make[1]: Leaving directory `/tmp/cabextract-1.1'
make: *** [install-am] Error 2



---

### Post by spyke01 on 2005-11-11
ok, i found out i had to run this:
```
sudo make install
```

and then everything worked fine ^^

---

