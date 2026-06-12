---
title: "binutils installation help"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by sanatan1988 on 2009-11-03
hello ,

i am trying to install a cross developement toolchain for arm.
found a script that will install the tool chain.

[http://embeddedlinuxinterfacing.com/chapters/03/buildtoolchain/](http://embeddedlinuxinterfacing.com/chapters/03/buildtoolchain/)

downloaded  [buildtoolchain-v1.21.tar.gz]("http://embeddedlinuxinterfacing.com/chapters/03/buildtoolchain/buildtoolchain-v1.21.tar.gz")
from the script

```

./configure --target=arm-linux --prefix=/usr/local

make
make install

```i got this:
> 
checking whether strstr is declared... yes
checking whether snprintf is declared... yes
checking whether vsnprintf is declared... yes
checking for library containing zlibVersion... no
checking linker --as-needed support... yes
checking for cos in -lm... yes
checking for ftello... yes
checking for ftello64... yes
checking for fseeko... yes
checking for fseeko64... yes
checking for fopen64... yes
checking size of off_t... 8
checking file_ptr type... BFD_HOST_64_BIT
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... yes
checking for madvise... yes
checking for mprotect... yes
configure: updating cache ./config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating bfd-in3.h
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing bfd_stdint.h commands
config.status: executing default commands
make[2]: Entering directory `/root/cross/builds/arm-linux-binutils/libiberty'
if [ x"" != x ] && [ ! -d pic ]; then \
      mkdir pic; \
    else true; fi
touch stamp-picdir
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/regex.c -o pic/regex.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/regex.c -o regex.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/cplus-dem.c -o pic/cplus-dem.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/cplus-dem.c -o cplus-dem.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/cp-demangle.c -o pic/cp-demangle.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/cp-demangle.c -o cp-demangle.o
../../binutils-2.20/libiberty/cp-demangle.c: In function &#8216;d_demangle_callback&#8217;:
../../binutils-2.20/libiberty/cp-demangle.c:4508: warning: &#8216;dc&#8217; may be used uninitialized in this function
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/md5.c -o pic/md5.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/md5.c -o md5.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/sha1.c -o pic/sha1.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/sha1.c -o sha1.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/alloca.c -o pic/alloca.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/alloca.c -o alloca.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/argv.c -o pic/argv.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/argv.c -o argv.o
if [ x"" != x ]; then \
      gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   ../../binutils-2.20/libiberty/choose-temp.c -o pic/choose-temp.o; \
    else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2  -I. -I../../binutils-2.20/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  ../../binutils-2.20/libiberty/choose-temp.c -o choose-temp.o



please help

thanks in advance

---

