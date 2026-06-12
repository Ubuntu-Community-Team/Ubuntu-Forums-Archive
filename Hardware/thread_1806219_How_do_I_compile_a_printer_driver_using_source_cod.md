---
title: "How do I compile a printer driver using source code?"
date: 2011-07-17
forum: Hardware
---

### Post by bwallum on 2011-07-17
Hi

I am trying to get a Canon Pixma MP492 running on Natty 64bit. Canon produce a driver for 32 bit but not 64 bit.

I have downloaded the source file, cnijfilter-source-3.20-1 and put it in a folder on the Desktop.

I have cd'd to the folder containing the Makefile and ran make. I get > bob@bob-desktop:~/Desktop/canon/cnijfilter-source-3.20-1$ make
for dir in libs cngpij pstocanonij backend backendnet cngpijmon/cnijnpr; do (cd $dir; make $target)|| exit 1; done
make[1]: Entering directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/libs'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: Leaving directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/libs'
make: *** [all] Error 1
 Anybody spot where I'm going wrong?

EDIT

I made some further progress (needed autoconf and automake) but still having problems> bob@bob-desktop:~/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter$ ./autogen.sh --program-suffix=mp490
processing .
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:         [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure --program-suffix=mp490 ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for socket... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating include/Makefile
config.status: creating include/cncl/Makefile
config.status: creating include/misc/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Now type `make' to compile the package.
bob@bob-desktop:~/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter$ make
make  all-recursive
make[1]: Entering directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter'
Making all in src
make[2]: Entering directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter/src'
gcc  -O2 -L../../358/libs_bin  -o cif bjferror.o bjfilter.o bjfimage.o bjfoption.o bjfpos.o bjfrcaccess.o getipc.o bjflist.o -lcnbpcmcm358 -lcnbpess358 -lm -ldl -ltiff -lpng -lcnbpcnclapi358 -lcnbpcnclbjcmd358 -lcnbpcnclui358 -lpopt 
/usr/bin/ld: skipping incompatible ../../358/libs_bin/libcnbpcmcm358.so when searching for -lcnbpcmcm358
/usr/bin/ld: cannot find -lcnbpcmcm358
/usr/bin/ld: skipping incompatible ../../358/libs_bin/libcnbpess358.so when searching for -lcnbpess358
/usr/bin/ld: cannot find -lcnbpess358
/usr/bin/ld: skipping incompatible ../../358/libs_bin/libcnbpcnclapi358.so when searching for -lcnbpcnclapi358
/usr/bin/ld: cannot find -lcnbpcnclapi358
/usr/bin/ld: skipping incompatible ../../358/libs_bin/libcnbpcnclbjcmd358.so when searching for -lcnbpcnclbjcmd358
/usr/bin/ld: cannot find -lcnbpcnclbjcmd358
/usr/bin/ld: skipping incompatible ../../358/libs_bin/libcnbpcnclui358.so when searching for -lcnbpcnclui358
/usr/bin/ld: cannot find -lcnbpcnclui358
collect2: ld returned 1 exit status
make[2]: *** [cif] Error 1
make[2]: Leaving directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bob/Desktop/canon/cnijfilter-source-3.20-1/cnijfilter'
make: *** [all] Error 2Can anybody help please?

---

