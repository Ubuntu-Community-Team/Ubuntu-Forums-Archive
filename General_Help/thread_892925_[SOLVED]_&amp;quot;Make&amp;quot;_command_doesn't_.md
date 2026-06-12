---
title: "[SOLVED] &amp;quot;Make&amp;quot; command doesn't work with Freeverb3."
date: 2008-08-17
forum: General Help
---

### Post by Diya on 2008-08-17
Please note that I've installed "build-essential", and made sure that I have "Make".

```
sudo apt-get install make

Reading package lists... Done
Building dependency tree       
Reading state information... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

The problem:
I'm trying to install freeverb3-2.2.1.

```
./configure

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking whether to build static libraries... no
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
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for fftw3f... no
checking for fftw3... no
checking for fftw3l... no
configure: error: *** any FFTW3 (single or double or ldouble) are not installed ***
```

Then make:
```
make

make: *** No targets specified and no makefile found.  Stop.
```

Even though there IS Makefile.in

How to fix this?

---

### Post by Diya on 2008-08-17
Is there any other way to install this program instead of "make"? It's not even in repositories.

---

### Post by Diya on 2008-08-20
Been 3 days, and still can't get it to work. I've tried rebooting, re-installing "make", etc, but nothing seems to work.

Any idea what might be wrong?

*bump*

---

### Post by Diya on 2008-08-22
```
checking for fftw3f... no
checking for fftw3... no
checking for fftw3l... no
configure: error: *** any FFTW3 (single or double or ldouble) are not installed ***
```

```
sudo apt-get install fftw3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libfftw3-3 instead of fftw3
**libfftw3-3 is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

:confused::confused::confused:

---

### Post by yabbadabbadont on 2008-08-22
Install fftw3-dev.  On Debian based systems, packages are usually split into the part needed at runtime and the one needed when building against it.  So anytime you run into a requirement for a library or other package, make sure that you install both the regular and development package.  The dev packages are usually named "packagebasename-dev".

---

### Post by Diya on 2008-08-22
> **yabbadabbadont said:**
> Install fftw3-dev.  On Debian based systems, packages are usually split into the part needed at runtime and the one needed when building against it.  So anytime you run into a requirement for a library or other package, make sure that you install both the regular and development package.  The dev packages are usually named "packagebasename-dev".

"Make" command works now, but I'm still getting some errors:

```
make
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure   --no-create --no-recursion
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
./configure: line 3159: AC_DISABLE_STATIC: command not found
./configure: line 3160: AC_PROG_LIBTOOL: command not found
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for fftw3f... yes
checking for fftw3f... yes
checking for fftw3... yes
checking for fftw3l... yes
./configure: line 5620: syntax error near unexpected token `1.0.0,,'
./configure: line 5620: `  AM_PATH_XMMS(1.0.0,,'
make: *** [config.status] Error 2
```

```
automake
audacious/Makefile.am:7: Libtool library used but `LIBTOOL' is undefined
audacious/Makefile.am:7: 
audacious/Makefile.am:7: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
audacious/Makefile.am:7: to `configure.in' and run `aclocal' and `autoconf' again.
audacious/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
audacious/Makefile.am:3: 
audacious/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
audacious/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
bmp/Makefile.am:7: Libtool library used but `LIBTOOL' is undefined
bmp/Makefile.am:7: 
bmp/Makefile.am:7: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
bmp/Makefile.am:7: to `configure.in' and run `aclocal' and `autoconf' again.
bmp/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
bmp/Makefile.am:3: 
bmp/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
bmp/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
double/Makefile.am:14: Libtool library used but `LIBTOOL' is undefined
double/Makefile.am:14: 
double/Makefile.am:14: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
double/Makefile.am:14: to `configure.in' and run `aclocal' and `autoconf' again.
double/Makefile.am:12: Libtool library used but `LIBTOOL' is undefined
double/Makefile.am:12: 
double/Makefile.am:12: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
double/Makefile.am:12: to `configure.in' and run `aclocal' and `autoconf' again.
float/Makefile.am:14: Libtool library used but `LIBTOOL' is undefined
float/Makefile.am:14: 
float/Makefile.am:14: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
float/Makefile.am:14: to `configure.in' and run `aclocal' and `autoconf' again.
float/Makefile.am:12: Libtool library used but `LIBTOOL' is undefined
float/Makefile.am:12: 
float/Makefile.am:12: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
float/Makefile.am:12: to `configure.in' and run `aclocal' and `autoconf' again.
freeverb/Makefile.am:64: Libtool library used but `LIBTOOL' is undefined
freeverb/Makefile.am:64: 
freeverb/Makefile.am:64: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
freeverb/Makefile.am:64: to `configure.in' and run `aclocal' and `autoconf' again.
ldouble/Makefile.am:14: Libtool library used but `LIBTOOL' is undefined
ldouble/Makefile.am:14: 
ldouble/Makefile.am:14: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
ldouble/Makefile.am:14: to `configure.in' and run `aclocal' and `autoconf' again.
ldouble/Makefile.am:12: Libtool library used but `LIBTOOL' is undefined
ldouble/Makefile.am:12: 
ldouble/Makefile.am:12: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
ldouble/Makefile.am:12: to `configure.in' and run `aclocal' and `autoconf' again.
libgdither/Makefile.am:1: Libtool library used but `LIBTOOL' is undefined
libgdither/Makefile.am:1: 
libgdither/Makefile.am:1: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libgdither/Makefile.am:1: to `configure.in' and run `aclocal' and `autoconf' again.
libsamplerate2/Makefile.am:5: Libtool library used but `LIBTOOL' is undefined
libsamplerate2/Makefile.am:5: 
libsamplerate2/Makefile.am:5: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libsamplerate2/Makefile.am:5: to `configure.in' and run `aclocal' and `autoconf' again.
xmms/Makefile.am:7: Libtool library used but `LIBTOOL' is undefined
xmms/Makefile.am:7: 
xmms/Makefile.am:7: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
xmms/Makefile.am:7: to `configure.in' and run `aclocal' and `autoconf' again.
xmms/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
xmms/Makefile.am:3: 
xmms/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
xmms/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
```

```
aclocal
aclocal:configure.in:303: warning: macro `AM_PATH_XMMS' not found in library
```
autoconf no problems.

What should I do now? Please help :(

---

### Post by yabbadabbadont on 2008-08-22
OK, you have build-essential installed, so I would suggest also installing the following:

autoconf
automake
bison
flex
libtool
intltool
xorg-dev

---

### Post by yabbadabbadont on 2008-08-22
I just had a look at the website, looks like you will also need the following:

libsamplerate-dev
libsndfile-dev
audacious-dev   <--- I'm assuming that you are going to use it with audacious.

---

### Post by Diya on 2008-08-22
> **yabbadabbadont said:**
> OK, you have build-essential installed, so I would suggest also installing the following:

autoconf
automake
bison
flex
libtool
intltool
xorg-dev

OK, I've installed them all. Still getting the same errors though.

```
configure.in:303: warning: macro `AM_PATH_XMMS' not found in library
```

I've searched "xmms" in Synaptic, and installed all the .dev that were unchecked. Still getting the same errors.

Any more ideas?

---

### Post by Diya on 2008-08-22
> **yabbadabbadont said:**
> I just had a look at the website, looks like you will also need the following:

libsamplerate-dev
libsndfile-dev
audacious-dev   <--- I'm assuming that you are going to use it with audacious.

Installed all of them, still getting the same error.

---

### Post by yabbadabbadont on 2008-08-22
I guess your next step is to ask for help from the developers over on sourceforge.

---

### Post by xeth_delta on 2008-08-22
> **Diya said:**
> Installed all of them, still getting the same error.

Wonder if this will help...
```
export AM_PATH_XMMS=/usr/lib/xmms
```
Then run configure again. If it does not work, please post lines 300-306 from configure.

---

### Post by Diya on 2008-08-22
> **xeth_delta said:**
> Wonder if this will help...
```
export AM_PATH_XMMS=/usr/lib/xmms
```
Then run configure again.
It didn't fix the error.

> **xeth_delta said:**
> If it does not work, please post lines 300-306 from configure.
Certain terminal code? Sorry, I'm a novice.

---

### Post by Diya on 2008-08-22
I've opened configure.in in gedit, and scrolled down to line 300-306
```
    AC_MSG_ERROR([*** GLIB >= 1.2.2 not installed - please install first ***]))
  AM_PATH_GTK(1.2.2,,
    AC_MSG_ERROR([*** GTK+ >= 1.2.2 not installed - please install first ***]))
  AM_PATH_XMMS(1.0.0,,
    AC_MSG_ERROR([*** XMMS >= 1.0.0 not installed - please install first ***]))
fi
```
I hope that's what you meant..

---

### Post by xeth_delta on 2008-08-22
Not really, I meant the contents of configure. It does not matter anyway, as I downloaded it to test and see if it works here. It does.

All I needed to install was fftw3-dev. configure worked after that.

The make errors you were getting refer to the fact that the configure process was not completed successfully.

Please have a look at a file called README. Have you installed all the dependencies mentioned in that file? Have you installed the xmms plugins?

[EDIT] What version of fftw3 did you download? I had a look at configure and the line where the error you posted is present, appears as an empty line over here.

Alternatively, remove the current fftw3 compilation directory, unpack again the tar file and configure again.

---

### Post by Diya on 2008-08-22
> **xeth_delta said:**
> Alternatively, remove the current fftw3 compilation directory, unpack again the tar file and configure again.
That worked!

I guess I've finally installed the program since the "make" and "make install" ended without errors. I don't know how to run the program though, and I can't find the freeverb plugins under audacious.

But that's something I'll figure out tomorrow since I'm extremely exhausted and mentally fatigued.

Thank you, both of you.

---

### Post by xeth_delta on 2008-08-22
> **Diya said:**
> That worked!

I guess I've finally installed the program since the "make" and "make install" ended without errors. I don't know how to run the program though, and I can't find the freeverb plugins under audacious.

But that's something I'll figure out tomorrow since I'm extremely exhausted and mentally fatigued.

Thank you, both of you.

You're most welcome.

You need to install with
```
sudo make install
```
If you choose to install in the directories where root permissions are needed (standard in most cases).
There is a way to make a deb package from the compiled code, I can show you that a tad later, though. I will post about it.

To locate where a program is installed
```
whereis program_name
```

---

### Post by Diya on 2008-08-23
Good morning!

> **xeth_delta said:**
> You need to install with
```
sudo make install
```
If you choose to install in the directories where root permissions are needed (standard in most cases).
That is what I did. Still can't find where is the program installed.
```
whereis freeverb3
freeverb3:
```
The program's plugins cannot be found under Audacious preferences whatsoever. Why is it such a *hassle* installing this program :confused:

---

### Post by xeth_delta on 2008-08-23
> **Diya said:**
> Good morning!


That is what I did. Still can't find where is the program installed.
```
whereis freeverb3
freeverb3:
```
The program's plugins cannot be found under Audacious preferences whatsoever. Why is it such a *hassle* installing this program :confused:

Are you sure that is the name of the resulting binary executable? It should be installed under /usr/local, with the executable in /usr/local/bin. Have a look in those places.
 Of course, if it is only a set of plugins, they would not be placed under bin. I am not familliar with the program itself.

---

### Post by Diya on 2008-08-23
> **xeth_delta said:**
> Are you sure that is the name of the resulting binary executable? It should be installed under /usr/local, with the executable in /usr/local/bin. Have a look in those places.

/usr/local/include/libfreeverb3-2/freeverb
Various "h" and "hpp" files there

/usr/local/lib
libfreeverb3.la
libfreeverb3.so
libfreeverb3.so.2
libfreeverb3.so.2.2.1

/usr/local/lib/pkgconfig
freeverb3.pc

What to do next?

~~~
You may skip this part: (Just me complaining.)
Shouldn't they include a throughout-installation-guide instead of the "generic" guide they use? Do they expect all Linux users to be experts?

I've been trying to install this 8 MBs application for 5 days in vain! Yes, I'm a complete novice when it comes to Linux OS, but I expect the programs to be more newbie-friendly, at least the guides included. 5 days is just way too much!

---

### Post by xeth_delta on 2008-08-23
> **Diya said:**
> /usr/local/include/libfreeverb3-2/freeverb
Various "h" and "hpp" files there

/usr/local/lib
libfreeverb3.la
libfreeverb3.so
libfreeverb3.so.2
libfreeverb3.so.2.2.1

/usr/local/lib/pkgconfig
freeverb3.pc

What to do next?

~~~
You may skip this part: (Just me complaining.)
Shouldn't they include a throughout-installation-guide instead of the "generic" guide they use? Do they expect all Linux users to be experts?

I've been trying to install this 8 MBs application for 5 days in vain! Yes, I'm a complete novice when it comes to Linux OS, but I expect the programs to be more newbie-friendly, at least the guides included. 5 days is just way too much!

The directory you found is just for development, hence the header files.
I understand your frustration, but that is why for almost any program there are package files which can easily be installed through the package management system (it can take, well... 2 minutes and one line of commands)

This, however does not seem to be the case with the program you try to install, which requires compilation. This is normally done in only a few steps, but sometimes there can be missing dependencies (as you could see) or complications. The solutions can not be necessarily obvious to a beginner, but we can try to help.

I will try to install the program myself on my machine to see what happens and come back with a new post.

---

### Post by xeth_delta on 2008-08-23
Ok, after further reading on their website it seems that it is just a library and plugin that is accessible from xmms/bmp/audacious, so really no surprise there is no executable compiled.

The installed files are the following:
```

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/freeverb3
/usr/share/doc/freeverb3/COPYING
/usr/share/doc/freeverb3/TODO
/usr/share/doc/freeverb3/NEWS
/usr/share/doc/freeverb3/README
/usr/share/doc/freeverb3/ChangeLog
/usr/share/doc/freeverb3/AUTHORS
/usr/share/doc/freeverb3/INSTALL
/usr/share/doc/freeverb3/doc
/usr/share/doc/freeverb3/doc/Makefile.in
/usr/share/doc/freeverb3/doc/Makefile.am
/usr/share/doc/freeverb3/doc/freeverb.orig.readme
/usr/share/doc/freeverb3/doc/Makefile
/usr/local
/usr/local/lib
/usr/local/lib/libfreeverb3.so.2.2.1
/usr/local/lib/libfreeverb3.la
/usr/local/lib/pkgconfig
/usr/local/lib/pkgconfig/freeverb3.pc
/usr/local/include
/usr/local/include/libsamplerate2
/usr/local/include/libsamplerate2/type_float.h
/usr/local/include/libsamplerate2/samplerate2_common.h
/usr/local/include/libsamplerate2/samplerate2.h
/usr/local/include/libsamplerate2/samplerate2_t.h
/usr/local/include/libfreeverb3-2
/usr/local/include/libfreeverb3-2/freeverb
/usr/local/include/libfreeverb3-2/freeverb/firfilter_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/comb_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/stenh_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/blockDelay.hpp
/usr/local/include/libfreeverb3-2/freeverb/stenh.hpp
/usr/local/include/libfreeverb3-2/freeverb/fv3_ns_end.h
/usr/local/include/libfreeverb3-2/freeverb/irmodels_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/allpass_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/rms.hpp
/usr/local/include/libfreeverb3-2/freeverb/revmodel_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/firwindow.hpp
/usr/local/include/libfreeverb3-2/freeverb/utils.hpp
/usr/local/include/libfreeverb3-2/freeverb/limitmodel_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodel_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/scomp.hpp
/usr/local/include/libfreeverb3-2/freeverb/tuning.h
/usr/local/include/libfreeverb3-2/freeverb/compmodel.hpp
/usr/local/include/libfreeverb3-2/freeverb/delay.hpp
/usr/local/include/libfreeverb3-2/freeverb/comb.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodels.hpp
/usr/local/include/libfreeverb3-2/freeverb/frag_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/fv3_type_float.h
/usr/local/include/libfreeverb3-2/freeverb/irmodel2.hpp
/usr/local/include/libfreeverb3-2/freeverb/firwindow_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodel3.hpp
/usr/local/include/libfreeverb3-2/freeverb/firfilter.hpp
/usr/local/include/libfreeverb3-2/freeverb/fv3_ns_start.h
/usr/local/include/libfreeverb3-2/freeverb/slimit.hpp
/usr/local/include/libfreeverb3-2/freeverb/irbase_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/utils_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/frag.hpp
/usr/local/include/libfreeverb3-2/freeverb/fir3bandsplit_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/rms_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/nrev.hpp
/usr/local/include/libfreeverb3-2/freeverb/fv3_defs.h
/usr/local/include/libfreeverb3-2/freeverb/scomp_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/src_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/allpass.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodel.hpp
/usr/local/include/libfreeverb3-2/freeverb/limitmodel.hpp
/usr/local/include/libfreeverb3-2/freeverb/irbase.hpp
/usr/local/include/libfreeverb3-2/freeverb/revmodel.hpp
/usr/local/include/libfreeverb3-2/freeverb/efilter_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/compmodel_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/fir3bandsplit.hpp
/usr/local/include/libfreeverb3-2/freeverb/blockDelay_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/delay_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/slimit_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodel2_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/src.hpp
/usr/local/include/libfreeverb3-2/freeverb/nrev_t.hpp
/usr/local/include/libfreeverb3-2/freeverb/efilter.hpp
/usr/local/include/libfreeverb3-2/freeverb/irmodel3_t.hpp
/usr/lib
/usr/lib/audacious
/usr/lib/audacious/Effect
/usr/lib/audacious/Effect/libmbcomp.so
/usr/lib/audacious/Effect/libimpulser2.so
/usr/lib/audacious/Effect/libfreeverb3.so
/usr/lib/audacious/Effect/libstenh.so
/usr/lib/audacious/Effect/libmbcomp.la
/usr/lib/audacious/Effect/libimpulser2.la
/usr/lib/audacious/Effect/libimpulser.la
/usr/lib/audacious/Effect/libfilter.so
/usr/lib/audacious/Effect/librevmodel.la
/usr/lib/audacious/Effect/libfilter.la
/usr/lib/audacious/Effect/librevmodel.so
/usr/lib/audacious/Effect/libstenh.la
/usr/lib/audacious/Effect/libfreeverb3.la
/usr/lib/audacious/Effect/libimpulser.so
/usr/local/lib/libfreeverb3.so
/usr/local/lib/libfreeverb3.so.2

```

What exactly do you need to use the library for? xmms/audacious/bmp?

I installed it on my computer and created a .deb package for it for easy administration and software database accounting. To do that:

```
sudo apt-get install checkinstall
```
Now to create a package from source code (this applies at least to any source code package that respects the standard configure, make and make install steps):

In this example, I assume I want to build and install the library and audacious plugin.

Enter the source directory
```
./configure --enable-audacious
make
checkinstall -install=no
```
It will ask you to fill some description for the .deb package you are building, write what you consider appropiate so that you know it is made by yourself. Follow the instructions, and in a few seconds a .deb package will written in the current directory. For some source packages you need to prepend "sudo" to checkinstall.

To install the package:
```
sudo dpkg -i package_name
```
Now it will be visible through apt-get, aptitude, synaptic, etc.

Let me know if you need further help.

---

### Post by Diya on 2008-08-24
It's finally working. Thank you! :)

---

### Post by Diya on 2008-08-24
Another problem though (Audacious):

Preferences --> Plugins --> "Effects" tab.
All the plugins there don't work, including Freeverb3.

:confused:

EDIT: Nevermind, it was just buggy.

---

### Post by xeth_delta on 2008-08-25
> **Diya said:**
> Another problem though (Audacious):

Preferences --> Plugins --> "Effects" tab.
All the plugins there don't work, including Freeverb3.

:confused:

EDIT: Nevermind, it was just buggy.

so, is it now working?

---

### Post by Diya on 2008-08-26
Yep!

---

### Post by xeth_delta on 2008-08-26
Great! :D Please remember to mark the thread as fixed.

---

