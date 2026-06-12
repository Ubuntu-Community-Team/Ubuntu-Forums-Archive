---
title: "Problems compiling YAPH"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by marco.voormolen on 2009-04-25
Hello all. I'm trying to compile the program YAPH (Yet Another Proxy Hunter). So far i've tried compiling several programs myself and failed every single time. I read my way through tons of tutorials, but still didn't succeed. Each time so far, I simply searched for an alternative, and in every case I found one. However, this program doesn't have an alternative so it seems. And therefore I'm hoping that someone here will be able to help me. 

When running sudo ./config I get the following:

> loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
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
checking if yaph should be compiled... yes
creating ./config.status
fast creating ./Makefile
fast creating yaph/Makefile
fast creating yaph/docs/Makefile
can't open ./yaph/docs/Makefile.in: No such file or directory
fast creating yaph/docs/en/Makefile
can't open ./yaph/docs/en/Makefile.in: No such file or directory
creating config.h
config.h is unchanged


When running 'sudo make' I get the following:

> make  all-recursive
make[1]: Entering directory `/usr/local/src/yaph-0.91'
Making all in yaph
make[2]: Entering directory `/usr/local/src/yaph-0.91/yaph'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make[2]: *** [init.o] Error 1
make[2]: Leaving directory `/usr/local/src/yaph-0.91/yaph'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/yaph-0.91'
make: *** [all-recursive-am] Error 2


And finally, when running 'make install', I get this:

> Making install in yaph
make[1]: Entering directory `/usr/local/src/yaph-0.91/yaph'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -O2   -c init.c
init.c: In function ‘init_options’:
init.c:203: error: label at end of compound statement
make[1]: *** [init.o] Error 1
make[1]: Leaving directory `/usr/local/src/yaph-0.91/yaph'
make: *** [install-recursive] Error 1


Can anyone help me out? Thanks in advance!

---

### Post by Partyboi2 on 2009-04-26
Hi, have a look at [[COLOR=Blue]this[/COLOR]]("http://en.allexperts.com/q/Unix-Linux-OS-1064/2008/5/configure-error-1.htm"), looks like  making a small change to yaph/init.c could work.

---

### Post by marco.voormolen on 2009-04-26
That worked perfectly! Thanks :)

---

