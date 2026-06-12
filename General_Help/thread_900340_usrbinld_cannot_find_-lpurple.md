---
title: "/usr/bin/ld: cannot find -lpurple"
date: 2008-08-25
forum: General Help
---

### Post by _Seven_ on 2008-08-25
Hi. I use Empathy IM and I'm trying to install telepathy-haze-0.2.1.tar.gz but when i execute the command 'make' appear this error : /usr/bin/ld: cannot find -lpurple

But i have already installed the libpurple-dev-2.4.1. I don't know why this is happening. Can anyone help me? Thank you

---

### Post by Paindistributor on 2008-08-25
Without seeing the makefile i'm not quite shure... but maybe you'll need the static libs of libpurple to compile it properly.

On my ubuntu system only shared libs are available.

```
$ find /usr -name 'libpurple*'
/usr/lib/libpurple.so.0.4.1
/usr/lib/libpurple.so.0
/usr/lib/libpurple-client.so.0
/usr/lib/libpurple-client.so.0.4.1

```

Compiling the code with static libs requires a 'libpurple.a' file. 
Check what kind of options configure has:

```
./configure --help
```

Post the output here and i'll take a look :)

---

### Post by _Seven_ on 2008-08-25
here is the output of ./configure --help

`configure' configures telepathy-haze 0.2.1 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
			  [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
			  [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/telepathy-haze]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-static[=PKGS]  build static libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-Werror        compile without -Werror (normally enabled in
                          development builds)
  --enable-leaky-request-stubs
                          print debugging information when libpurple attempts
                          to use the request API (warning: very leaky)

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-tags[=TAGS]      include additional configurations [automatic]

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CXXCPP      C++ preprocessor
  F77         Fortran 77 compiler command
  FFLAGS      Fortran 77 compiler flags
  PKG_CONFIG  path to pkg-config utility
  PURPLE_CFLAGS
              C compiler flags for PURPLE, overriding pkg-config
  PURPLE_LIBS linker flags for PURPLE, overriding pkg-config
  TP_GLIB_CFLAGS
              C compiler flags for TP_GLIB, overriding pkg-config
  TP_GLIB_LIBS
              linker flags for TP_GLIB, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to <https://bugs.freedesktop.org/enter_bug.cgi?product=Telepathy&component=telepathy-haze>.

Thank you for your help

---

### Post by _Seven_ on 2008-08-25
In my system using the command find /usr -name 'libpurple*' i got:

/usr/include/libpurple
/usr/share/lintian/overrides/libpurple0
/usr/share/lintian/overrides/libpurple-bin
/usr/share/doc/libpurple-dev
/usr/share/doc/libpurple0
/usr/share/doc/libpurple-bin
/usr/lib/libpurple.so
/usr/lib/libpurple-client.so.0
/usr/lib/libpurple.so.0
/usr/lib/libpurple-client.so.0.5.0
/usr/lib/libpurple-client.so
/usr/lib/libpurple.so.0.5.0

---

### Post by Paindistributor on 2008-08-25
Hm... there's nothing to customize here. Can you post the output of configure?

```
./configure
```

---

### Post by _Seven_ on 2008-08-25
here:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC
checking if gcc -std=gnu99 PIC flag -fPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Werror... yes
checking to see if compiler understands -Wextra... yes
checking to see if compiler understands -Wno-missing-field-initializers... yes
checking to see if compiler understands -Wno-unused-parameter... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PURPLE... yes
checking for TP_GLIB... yes
checking for tp_debug_divert_messages in -ltelepathy-glib... yes
checking for purple_dbus_uninit in -lpurple... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating m4/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

---

### Post by Paindistributor on 2008-08-25
After thinking around the problem i tried to compile telepathy-haze by myself. Most interesting part is the last line. We got differences here. The lib compiles without errors on my system.

```
checking for PURPLE... yes
checking for TP_GLIB... yes
checking for tp_debug_divert_messages in -ltelepathy-glib... yes
checking for purple_dbus_uninit in -lpurple... yes

```

I'm running the latest Ubuntu 8.04 (Hardy Heron). What version are you running?

---

### Post by _Seven_ on 2008-08-25
My version is 8.04 too :) i can't figure out why this is happening

---

### Post by Paindistributor on 2008-08-26
Are you using a 32bit or a 64bit system? Perhaps we just should compare our systems. At least, something must be different :roll:

```
$ uname -a

Linux mikoto 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

```
$ aptitude show libpurple-dev

Paket: libpurple-dev
Zustand: Installiert
Automatisch installiert: ja
Version: 1:2.4.1-1ubuntu2.1
Priorität: optional
Bereich: libdevel
Verwalter: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Unkomprimierte Größe: 1044k
Hängt ab von: libdbus-glib-1-dev, libglib2.0-dev, libpurple0 (>= 1:2.4.1-1ubuntu2.1), pkg-config
Kollidiert mit: pidgin-dev (< 1:2.1.1-2)
Ersetzt: pidgin-dev (< 1:2.1.1-2)
Beschreibung: multi-protocol instant messaging library - development files
 This package contains the headers and other development files not included in the main libpurple0 package. Install this if you wish to
 compile your own client-agnostic plugins, or would like to compile programs that use libpurple.
Homepage: http://www.pidgin.im
```

---

### Post by hackel on 2008-09-12
I had this problem, and discovered the cause was mismatched versions of libpurple0 and libpurple-dev.  I had installed the getdeb version of libpurple0, but they don't provide -dev packages so I still had the older repository -dev packages installed.  I downgraded everything back to the repository version, and everything configured and compiled fine.

---

### Post by ov1d1u on 2009-09-15
GetDeb also provide -dev packgages, even they do not appear on their website. For example, the -dev packages for libpurple can be found there: [http://archive.getdeb.net/getdeb/ubuntu/jaunty/li/](http://archive.getdeb.net/getdeb/ubuntu/jaunty/li/)

---

