---
title: "Artec AS6E scanner"
date: 2009-07-29
forum: Hardware
---

### Post by lowvoice on 2009-07-29
I have downloaded the drivers from SANE and have tried to install it in terminal however the scanner is still not working 

matt@matt-desktop:~$ /home/matt/Desktop/as6edriver-0.5/configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... (cached) gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking whether  supports -frepo... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking how to recognise dependant libraries... (cached) pass_all
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... (cached) yes
checking for objdir... .libs
checking for gcc option to produce PIC...  -fPIC -DPIC
checking if gcc PIC flag  -fPIC -DPIC works... (cached) yes
checking if gcc static flag -static works... (cached) yes
finding the maximum length of command line arguments... (cached) 73729
checking if gcc supports -c -o file.o... (cached) yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
creating libtool
loading cache ./config.cache
checking for object suffix... (cached) o
checking for executable suffix... (cached) no
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for extra includes... no
checking for extra libs... no
checking if as6edriver should be compiled... yes
creating ./config.status
fast creating ./Makefile
fast creating as6edriver/Makefile
fast creating as6edriver/docs/Makefile
can't open /home/matt/Desktop/as6edriver-0.5/as6edriver/docs/Makefile.in: No such file or directory
fast creating as6edriver/docs/en/Makefile
can't open /home/matt/Desktop/as6edriver-0.5/as6edriver/docs/en/Makefile.in: No such file or directory
creating config.h
config.h is unchanged
matt@matt-desktop:~$ make
make  all-recursive
make[1]: Entering directory `/home/matt'
Making all in as6edriver
make[2]: Entering directory `/home/matt/as6edriver'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matt/as6edriver'
make[2]: Entering directory `/home/matt'
make[2]: Leaving directory `/home/matt'
make[1]: Leaving directory `/home/matt'
matt@matt-desktop:~$ make install (as root)
bash: syntax error near unexpected token `('
matt@matt-desktop:~$ make install
Making install in as6edriver
make[1]: Entering directory `/home/matt/as6edriver'
make[2]: Entering directory `/home/matt/as6edriver'
/bin/sh /home/matt/Desktop/as6edriver-0.5/admin/mkinstalldirs /usr/local/bin
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -p   as6edriver /usr/local/bin/as6edriver
/usr/bin/install -c -p as6edriver /usr/local/bin/as6edriver
/usr/bin/install: cannot create regular file `/usr/local/bin/as6edriver': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/matt/as6edriver'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/matt/as6edriver'
make: *** [install-recursive] Error 1
matt@matt-desktop:~$

---

### Post by lowvoice on 2009-08-05
Bumpity bump

---

