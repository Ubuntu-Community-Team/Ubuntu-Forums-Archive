---
title: "Custom install problems."
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by GroogFish on 2009-09-12
I've downloaded a fps program. The readme installation instructions say-

> libglfps  Copyright 2004  Matthew Mueller <donut AT dakotacom DOT net>


Description:
  libglfps adds a framerate display to OpenGL apps that don't have one built
in, through the magic of LD_PRELOAD.  (Similar to FRAPS on Windows.)


Requirements:
  OpenGL, GLUT, GLX.


Installation:
  ./configure
  make install


Usage:
  glfps <program> [program args]


Notes:
  Currently, libglfps only supports apps that use double buffering.
  Also, it has only been tested on Linux with glibc2.  Reports of results on
other operating systems welcome.

So I unpacked the archive.
"Selected"? it (cd ./Desktop/location)
Then ran ./config (ran successfully)
Then I tired to run...
-make install
-install
-make
-./configure; make; make install
-./configure; make install
-/configure; install
etc.
etc.
etc.

And nothing is working. I keep getting this message-

> micah@micah-comp:~/Desktop/libglfps-0.1$ ./configure; make; make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


What now?

---

### Post by wojox on 2009-09-12
Download G++

```
sudo apt-get install g++
```

---

### Post by Shazaam on 2009-09-12
Also (you probably already know this)...
```
./configure
make
sudo make install
```

---

### Post by GroogFish on 2009-09-12
Installed g++ and ran this code-

```

./configure; make; sudo make install

```

and got another error

> micah@micah-comp:~/Desktop/libglfps-0.1$ ./configure; make; sudo make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating wrapper/Makefile
config.status: creating wrapper/glfps
config.status: executing depfiles commands
Making all in src
make[1]: Entering directory `/home/micah/Desktop/libglfps-0.1/src'
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"libglfps\" -DPACKAGE_TARNAME=\"libglfps\" -DPACKAGE_VERSION=\"0.1\" -DPACKAGE_STRING=\"libglfps\ 0.1\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libglfps\" -DVERSION=\"0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -I. -I.     -g -O2 -Wall -MT glfps.lo -MD -MP -MF ".deps/glfps.Tpo" -c -o glfps.lo glfps.c; \
    then mv -f ".deps/glfps.Tpo" ".deps/glfps.Plo"; else rm -f ".deps/glfps.Tpo"; exit 1; fi
 gcc -DPACKAGE_NAME=\"libglfps\" -DPACKAGE_TARNAME=\"libglfps\" -DPACKAGE_VERSION=\"0.1\" "-DPACKAGE_STRING=\"libglfps 0.1\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libglfps\" -DVERSION=\"0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -g -O2 -Wall -MT glfps.lo -MD -MP -MF .deps/glfps.Tpo -c glfps.c  -fPIC -DPIC -o .libs/glfps.o
glfps.c:43:19: error: GL/gl.h: No such file or directory
glfps.c:44:21: error: GL/glut.h: No such file or directory
glfps.c:45:20: error: GL/glx.h: No such file or directory
glfps.c:58: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'textlist'
glfps.c: In function 'update_fps':
glfps.c:72: error: 'textlist' undeclared (first use in this function)
glfps.c:72: error: (Each undeclared identifier is reported only once
glfps.c:72: error: for each function it appears in.)
glfps.c:73: warning: implicit declaration of function 'glGenLists'
glfps.c:75: warning: implicit declaration of function 'glNewList'
glfps.c:75: error: 'GL_COMPILE' undeclared (first use in this function)
glfps.c:77: warning: implicit declaration of function 'glutStrokeCharacter'
glfps.c:77: error: 'GLUT_STROKE_MONO_ROMAN' undeclared (first use in this function)
glfps.c:79: warning: implicit declaration of function 'glEndList'
glfps.c:83: warning: implicit declaration of function 'glGetIntegerv'
glfps.c:83: error: 'GL_VIEWPORT' undeclared (first use in this function)
glfps.c:85: warning: implicit declaration of function 'glPushAttrib'
glfps.c:85: error: 'GL_CURRENT_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_ENABLE_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_TRANSFORM_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_LINE_BIT' undeclared (first use in this function)
glfps.c:87: warning: implicit declaration of function 'glDisable'
glfps.c:87: error: 'GL_LIGHTING' undeclared (first use in this function)
glfps.c:88: error: 'GL_ALPHA_TEST' undeclared (first use in this function)
glfps.c:89: error: 'GL_DEPTH_TEST' undeclared (first use in this function)
glfps.c:90: error: 'GL_BLEND' undeclared (first use in this function)
glfps.c:91: error: 'GL_FOG' undeclared (first use in this function)
glfps.c:93: error: 'GL_LINE_STIPPLE' undeclared (first use in this function)
glfps.c:94: error: 'GL_LINE_SMOOTH' undeclared (first use in this function)
glfps.c:95: warning: implicit declaration of function 'glLineWidth'
glfps.c:97: warning: implicit declaration of function 'glMatrixMode'
glfps.c:97: error: 'GL_PROJECTION' undeclared (first use in this function)
glfps.c:98: warning: implicit declaration of function 'glPushMatrix'
glfps.c:99: warning: implicit declaration of function 'glLoadIdentity'
glfps.c:100: warning: implicit declaration of function 'glOrtho'
glfps.c:103: error: 'GL_MODELVIEW' undeclared (first use in this function)
glfps.c:109: warning: implicit declaration of function 'glColor3f'
glfps.c:111: warning: implicit declaration of function 'glTranslatef'
glfps.c:112: warning: implicit declaration of function 'glScalef'
glfps.c:113: warning: implicit declaration of function 'glCallList'
glfps.c:114: warning: implicit declaration of function 'glPopMatrix'
glfps.c:125: warning: implicit declaration of function 'glPopAttrib'
glfps.c: At top level:
glfps.c:128: error: expected ')' before '*' token
glfps.c:129: error: expected ')' before '*' token
make[1]: *** [glfps.lo] Error 1
make[1]: Leaving directory `/home/micah/Desktop/libglfps-0.1/src'
make: *** [all-recursive] Error 1
Making install in src
make[1]: Entering directory `/home/micah/Desktop/libglfps-0.1/src'
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"libglfps\" -DPACKAGE_TARNAME=\"libglfps\" -DPACKAGE_VERSION=\"0.1\" -DPACKAGE_STRING=\"libglfps\ 0.1\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libglfps\" -DVERSION=\"0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -I. -I.     -g -O2 -Wall -MT glfps.lo -MD -MP -MF ".deps/glfps.Tpo" -c -o glfps.lo glfps.c; \
    then mv -f ".deps/glfps.Tpo" ".deps/glfps.Plo"; else rm -f ".deps/glfps.Tpo"; exit 1; fi
 gcc -DPACKAGE_NAME=\"libglfps\" -DPACKAGE_TARNAME=\"libglfps\" -DPACKAGE_VERSION=\"0.1\" "-DPACKAGE_STRING=\"libglfps 0.1\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libglfps\" -DVERSION=\"0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -g -O2 -Wall -MT glfps.lo -MD -MP -MF .deps/glfps.Tpo -c glfps.c  -fPIC -DPIC -o .libs/glfps.o
glfps.c:43:19: error: GL/gl.h: No such file or directory
glfps.c:44:21: error: GL/glut.h: No such file or directory
glfps.c:45:20: error: GL/glx.h: No such file or directory
glfps.c:58: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'textlist'
glfps.c: In function 'update_fps':
glfps.c:72: error: 'textlist' undeclared (first use in this function)
glfps.c:72: error: (Each undeclared identifier is reported only once
glfps.c:72: error: for each function it appears in.)
glfps.c:73: warning: implicit declaration of function 'glGenLists'
glfps.c:75: warning: implicit declaration of function 'glNewList'
glfps.c:75: error: 'GL_COMPILE' undeclared (first use in this function)
glfps.c:77: warning: implicit declaration of function 'glutStrokeCharacter'
glfps.c:77: error: 'GLUT_STROKE_MONO_ROMAN' undeclared (first use in this function)
glfps.c:79: warning: implicit declaration of function 'glEndList'
glfps.c:83: warning: implicit declaration of function 'glGetIntegerv'
glfps.c:83: error: 'GL_VIEWPORT' undeclared (first use in this function)
glfps.c:85: warning: implicit declaration of function 'glPushAttrib'
glfps.c:85: error: 'GL_CURRENT_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_ENABLE_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_TRANSFORM_BIT' undeclared (first use in this function)
glfps.c:85: error: 'GL_LINE_BIT' undeclared (first use in this function)
glfps.c:87: warning: implicit declaration of function 'glDisable'
glfps.c:87: error: 'GL_LIGHTING' undeclared (first use in this function)
glfps.c:88: error: 'GL_ALPHA_TEST' undeclared (first use in this function)
glfps.c:89: error: 'GL_DEPTH_TEST' undeclared (first use in this function)
glfps.c:90: error: 'GL_BLEND' undeclared (first use in this function)
glfps.c:91: error: 'GL_FOG' undeclared (first use in this function)
glfps.c:93: error: 'GL_LINE_STIPPLE' undeclared (first use in this function)
glfps.c:94: error: 'GL_LINE_SMOOTH' undeclared (first use in this function)
glfps.c:95: warning: implicit declaration of function 'glLineWidth'
glfps.c:97: warning: implicit declaration of function 'glMatrixMode'
glfps.c:97: error: 'GL_PROJECTION' undeclared (first use in this function)
glfps.c:98: warning: implicit declaration of function 'glPushMatrix'
glfps.c:99: warning: implicit declaration of function 'glLoadIdentity'
glfps.c:100: warning: implicit declaration of function 'glOrtho'
glfps.c:103: error: 'GL_MODELVIEW' undeclared (first use in this function)
glfps.c:109: warning: implicit declaration of function 'glColor3f'
glfps.c:111: warning: implicit declaration of function 'glTranslatef'
glfps.c:112: warning: implicit declaration of function 'glScalef'
glfps.c:113: warning: implicit declaration of function 'glCallList'
glfps.c:114: warning: implicit declaration of function 'glPopMatrix'
glfps.c:125: warning: implicit declaration of function 'glPopAttrib'
glfps.c: At top level:
glfps.c:128: error: expected ')' before '*' token
glfps.c:129: error: expected ')' before '*' token
make[1]: *** [glfps.lo] Error 1
make[1]: Leaving directory `/home/micah/Desktop/libglfps-0.1/src'
make: *** [install-recursive] Error 1
micah@micah-comp:~/Desktop/libglfps-0.1$ 


---

