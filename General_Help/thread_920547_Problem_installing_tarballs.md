---
title: "Problem installing tarballs"
date: 2008-09-15
forum: General Help
---

### Post by Mashy on 2008-09-15
Hi. I am using Hardy at the moment. 
I have noticed that whenever I try to install a tarball, I extract it, then cd to the directory, and then type ./configure.
After this, I have been told that I should type 'make'. There is one problem though. Every time I have ever tried this it always comes up with 

```
make: *** No targets specified and no makefile found. Stop.
```

Before now I have always encountered this, shrugged, and then found the program that I wanted from a repository or I've found a .deb file, but I cannot find either for this program (almanah, a sort of diary thing) so this is the only way that I can install it.
It's not too much of a problem, but I imagine that because I cannot do this then there is something wrong with my computer. Or maybe I'm doing it wrong, I dunno.

Any help with this will be much appreciated.
Thanks.

---

### Post by bigO on 2008-09-15
post the output after you enter ./configure please. We might be able to see what the problem is from that.

---

### Post by IllegalCharacter on 2008-09-15
Also, not all tarballs come with ./configure and make. A lot of them nowadays are using other systems like scons. You should check the README or INSTALL files that usually come inside the tarball to see how to install it.

There's also the issues of dependencies. The code you're compiling (when you do ./configure and make, you're compiling the code) may depend on other libraries like GTK, ALSA, etc.

When you run ./configure, it should say any errors when it quits. It will tell you which libraries you need. To install them, go to System->Administration->Synaptic Package Manager and search for them there. Install the one(s) that have -dev in them, as those are the versions that you need for compiling.

Also a lot of things require the build-essential package, install that if you haven't already.

---

### Post by forger on 2008-09-15
What program are you trying to compile?
Link?

---

### Post by Mashy on 2008-09-15
All of the programs that I have tried to install in this way have told me to do so in the readme/installation instructions/whatever file.

From ./configure

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for STANDARD... configure: error: Package requirements (glib-2.0 gtk+-2.0 >= 2.12 gmodule-2.0 gio-2.0 sqlite3 gtkspell-2.0 cairo) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'gio-2.0' found
No package 'sqlite3' found
No package 'gtkspell-2.0' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables STANDARD_CFLAGS
and STANDARD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'm guessing that I should install the files near the bottom where it says 'no *** file found'?

---

### Post by iponeverything on 2008-09-15
You are right. try:

apt-get install glib-2.0 gtk+-2.0 gmodule-2.0 gio-2.0 sqlite3 gtkspell-2.0 cairo


then try the configure..

---

### Post by Mashy on 2008-09-15
Tried that, and I get back

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-2.0

```

I've searched for 'glib' in synaptic, but anything that looks hopefull it says that I already have installed.

Edit: Have tried the above for each of the things individually and it could find none of the packages, except sqlite, but it says I already have the newest version of that. 
Confusing.

---

### Post by forger on 2008-09-16
You still haven't answered what you're trying to compile.. maybe there's an already compiled version and a .deb package somewhere in the Internet.

By the way, you are compiling, which means you are **developing**, so you need the **-dev** packages
```

apt-cache search sqlite.*dev
apt-cache search glib.*2.0
apt-cache search gtk.*2.0.*dev
```
..and so on

```
sudo apt-get install libglib2.0-dev libsqlite3-dev libgtk2.0-dev libcairo2-dev libcairomm-1.0-dev libgvfscommon-dev libgtkspell-dev
```

I couldn't find gmodule-2.0 but i think it's in the gvfs common

---

