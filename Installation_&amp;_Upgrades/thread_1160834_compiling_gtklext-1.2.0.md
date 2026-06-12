---
title: "compiling gtklext-1.2.0"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Oblivion_4 on 2009-05-16
Hi there,
I am trying to install a program called gtklext-1.2.0 from source on my computer which is a requirement to install cairo-dock 2.0.0 from source. When I attempt to configure the program I receive an error stating "configure: error: X development libraries not found"

now I have been reading alot about the X development libraries and apparently there are several of them and I'd rather not go hunt down them all. Here is the output of the configure

```
 ./configure --prefix=/opt/gtk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for strerror in -lcposix... no
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for native Win32... no
checking whether build environment is sane... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for gawk... (cached) mawk
checking for perl5... no
checking for perl... /usr/bin/perl
checking for indent... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.20.1)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.16.0)
checking for ANSI C header files... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for memset... yes
checking for sqrt... yes
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking gdk/gdkdisplay.h usability... yes
checking gdk/gdkdisplay.h presence... yes
checking for gdk/gdkdisplay.h... yes
checking gdk/gdkscreen.h usability... yes
checking gdk/gdkscreen.h presence... yes
checking for gdk/gdkscreen.h... yes
checking for gdk_display_get_default in GDK library... yes
configure: GDK supports multihead
checking for gdk_x11_colormap_foreign_new... yes
checking for X... no
configure: error: X development libraries not found

```

Any help would be appreciated.

---

### Post by Oblivion_4 on 2009-05-16
I eventually gave up on compiling and retrieved the library using apt-get instead

---

