---
title: "Building - pcsx2 Assistance"
date: 2008-08-25
forum: General Help
---

### Post by Deten on 2008-08-25
I am new to building stuff, along with my only having used ubuntu for about 8months.

So I am trying to build pcsx2 and have followed alot of the guides here and on other sites.

Is there any way someone could take a look at my output and help me learn what to look for, and **_how to find dev's that I am missing_**  which is probably the most important thing because its giving me the most trouble :)

So here we go, I am terribly sorry its so long, but I guess you have to learn somehow:

```
deten@deten-laptop:~$ cd pcsx2
deten@deten-laptop:~/pcsx2$ sudo sh build.sh all
[sudo] password for deten: 
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Linux/Makefile.am:5: shell pkg-config --cflags gtk+-2.0: non-POSIX variable name
Linux/Makefile.am:5: (probably a GNU make extension)
Linux/Makefile.am:6: compiling `callbacks.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lGLEW... yes
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF .deps/libZeroGSLinux_a-callbacks.Tpo -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c
mv -f .deps/libZeroGSLinux_a-callbacks.Tpo .deps/libZeroGSLinux_a-callbacks.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
mv -f .deps/libZeroGSLinux_a-Conf.Tpo .deps/libZeroGSLinux_a-Conf.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-interface.o -MD -MP -MF .deps/libZeroGSLinux_a-interface.Tpo -c -o libZeroGSLinux_a-interface.o `test -f 'interface.c' || echo './'`interface.c
mv -f .deps/libZeroGSLinux_a-interface.Tpo .deps/libZeroGSLinux_a-interface.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Linux.o -MD -MP -MF .deps/libZeroGSLinux_a-Linux.Tpo -c -o libZeroGSLinux_a-Linux.o `test -f 'Linux.cpp' || echo './'`Linux.cpp
Linux.cpp: In function ‘void GSconfigure()’:
Linux.cpp:240: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:243: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:246: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:249: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:252: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:255: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:258: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:261: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:264: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:267: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:270: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:273: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:276: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:279: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:282: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:285: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:288: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:291: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:294: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:297: warning: deprecated conversion from string constant to ‘char*’
Linux.cpp:300: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroGSLinux_a-Linux.Tpo .deps/libZeroGSLinux_a-Linux.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-support.o -MD -MP -MF .deps/libZeroGSLinux_a-support.Tpo -c -o libZeroGSLinux_a-support.o `test -f 'support.c' || echo './'`support.c
mv -f .deps/libZeroGSLinux_a-support.Tpo .deps/libZeroGSLinux_a-support.Po
rm -f libZeroGSLinux.a
ar cru libZeroGSLinux.a libZeroGSLinux_a-callbacks.o libZeroGSLinux_a-Conf.o libZeroGSLinux_a-interface.o libZeroGSLinux_a-Linux.o libZeroGSLinux_a-support.o 
ranlib libZeroGSLinux.a
make[2]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
make[1]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making install in .
make[1]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-GSmain.o -MD -MP -MF .deps/libZeroGSogl_a-GSmain.Tpo -c -o libZeroGSogl_a-GSmain.o `test -f 'GSmain.cpp' || echo './'`GSmain.cpp
GSmain.cpp:74: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSsetGameCRC(int, int)’:
GSmain.cpp:169: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘s32 GSinit()’:
GSmain.cpp:273: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:277: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:290: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘s32 GSopen(void*, char*, int)’:
GSmain.cpp:600: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:614: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:619: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:634: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSvsync(int)’:
GSmain.cpp:765: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void _GSgifTransfer(pathInfo*, u32*, u32)’:
GSmain.cpp:978: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:992: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp:1096: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void GSgifTransfer1(u32*, u32)’:
GSmain.cpp:1162: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘s32 GSfreeze(int, freezeData*)’:
GSmain.cpp:1209: warning: deprecated conversion from string constant to ‘char*’
GSmain.cpp: In function ‘void DVProfEnd(u32)’:
GSmain.cpp:1341: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroGSogl_a-GSmain.Tpo .deps/libZeroGSogl_a-GSmain.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-memcpy_amd.o -MD -MP -MF .deps/libZeroGSogl_a-memcpy_amd.Tpo -c -o libZeroGSogl_a-memcpy_amd.o `test -f 'memcpy_amd.cpp' || echo './'`memcpy_amd.cpp
memcpy_amd.cpp:96:26: warning: missing terminating ' character
memcpy_amd.cpp:101:30: warning: missing terminating ' character
memcpy_amd.cpp:107:38: warning: missing terminating ' character
memcpy_amd.cpp:164:38: warning: missing terminating ' character
memcpy_amd.cpp:226:37: warning: missing terminating ' character
memcpy_amd.cpp:274:53: warning: missing terminating ' character
memcpy_amd.cpp:277:34: warning: missing terminating ' character
mv -f .deps/libZeroGSogl_a-memcpy_amd.Tpo .deps/libZeroGSogl_a-memcpy_amd.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-Regs.o -MD -MP -MF .deps/libZeroGSogl_a-Regs.Tpo -c -o libZeroGSogl_a-Regs.o `test -f 'Regs.cpp' || echo './'`Regs.cpp
mv -f .deps/libZeroGSogl_a-Regs.Tpo .deps/libZeroGSogl_a-Regs.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-x86.o -MD -MP -MF .deps/libZeroGSogl_a-x86.Tpo -c -o libZeroGSogl_a-x86.o `test -f 'x86.cpp' || echo './'`x86.cpp
mv -f .deps/libZeroGSogl_a-x86.Tpo .deps/libZeroGSogl_a-x86.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-zpipe.o -MD -MP -MF .deps/libZeroGSogl_a-zpipe.Tpo -c -o libZeroGSogl_a-zpipe.o `test -f 'zpipe.cpp' || echo './'`zpipe.cpp
mv -f .deps/libZeroGSogl_a-zpipe.Tpo .deps/libZeroGSogl_a-zpipe.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-Mem.o -MD -MP -MF .deps/libZeroGSogl_a-Mem.Tpo -c -o libZeroGSogl_a-Mem.o `test -f 'Mem.cpp' || echo './'`Mem.cpp
mv -f .deps/libZeroGSogl_a-Mem.Tpo .deps/libZeroGSogl_a-Mem.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-rasterfont.o -MD -MP -MF .deps/libZeroGSogl_a-rasterfont.Tpo -c -o libZeroGSogl_a-rasterfont.o `test -f 'rasterfont.cpp' || echo './'`rasterfont.cpp
mv -f .deps/libZeroGSogl_a-rasterfont.Tpo .deps/libZeroGSogl_a-rasterfont.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-targets.o -MD -MP -MF .deps/libZeroGSogl_a-targets.Tpo -c -o libZeroGSogl_a-targets.o `test -f 'targets.cpp' || echo './'`targets.cpp
targets.cpp: In member function ‘virtual void ZeroGS::CRenderTarget::Update(int, ZeroGS::CRenderTarget*)’:
targets.cpp:318: warning: deprecated conversion from string constant to ‘char*’
targets.cpp:323: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘virtual void ZeroGS::CRenderTarget::ConvertTo32()’:
targets.cpp:438: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘virtual void ZeroGS::CRenderTarget::ConvertTo16()’:
targets.cpp:563: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘void ZeroGS::CRenderTarget::_CreateFeedback()’:
targets.cpp:707: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘virtual bool ZeroGS::CDepthTarget::Create(const frameInfo&)’:
targets.cpp:815: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘ZeroGS::CMemoryTarget* ZeroGS::CMemoryTargetMngr::GetMemoryTarget(const tex0Info&, int)’:
targets.cpp:1627: warning: deprecated conversion from string constant to ‘char*’
targets.cpp:1720: warning: deprecated conversion from string constant to ‘char*’
targets.cpp:2031: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In member function ‘u32 ZeroGS::CBitwiseTextureMngr::GetTexInt(u32, u32)’:
targets.cpp:2197: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In function ‘void ZeroGS::TransferHostLocal(const void*, u32)’:
targets.cpp:2576: warning: deprecated conversion from string constant to ‘char*’
targets.cpp: In function ‘void ZeroGS::GetRectMemAddress(int&, int&, int, int, int, int, int, int, int)’:
targets.cpp:3088: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroGSogl_a-targets.Tpo .deps/libZeroGSogl_a-targets.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSogl_a-zerogs.o -MD -MP -MF .deps/libZeroGSogl_a-zerogs.Tpo -c -o libZeroGSogl_a-zerogs.o `test -f 'zerogs.cpp' || echo './'`zerogs.cpp
zerogs.cpp:321: warning: non-local variable ‘<anonymous union> g_vars’ uses anonymous type
zerogs.cpp: In function ‘void HandleCgError(_CGcontext*, CGerror, void*)’:
zerogs.cpp:857: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::HandleGLError()’:
zerogs.cpp:891: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:894: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:900: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:903: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:906: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:909: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:912: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:915: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘bool ZeroGS::Create(int, int)’:
zerogs.cpp:1088: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1092: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1096: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1116: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1133: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1155: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1185: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1187: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1189: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1204: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1232: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1238: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1242: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1250: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1258: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1263: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1272: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1276: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1296: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1318: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1363: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1367: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1371: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1401: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1406: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1414: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1419: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1474: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1484: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1533: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1547: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1567: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1590: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1612: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1631: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1632: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1654: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1662: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1663: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1665: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1667: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::Destroy(BOOL)’:
zerogs.cpp:1704: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1773: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::ChangeDeviceSize(int, int)’:
zerogs.cpp:1890: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:1892: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘bool ZeroGS::LoadExtraEffects()’:
zerogs.cpp:2165: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2165: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2166: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2166: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2168: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2168: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2169: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2169: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2176: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2176: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2181: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2181: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2182: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2182: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2185: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2185: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2188: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2188: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2193: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2193: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2194: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2194: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2196: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2197: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2197: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2199: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2199: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2200: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2200: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2201: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2201: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2204: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2204: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2208: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2208: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2209: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2209: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2212: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2212: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2216: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2218: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2218: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2219: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2219: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2220: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2220: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2221: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2221: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2222: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2222: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2223: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2223: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘FRAGMENTSHADER* ZeroGS::LoadShadeEffect(int, int, int, int, int, const clampInfo&, int, bool*)’:
zerogs.cpp:2266: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2277: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2285: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::Flush(int)’:
zerogs.cpp:2579: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:2706: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:3012: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:3025: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::RenderCustom(float)’:
zerogs.cpp:3417: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:3474: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::RenderCRTC(int)’:
zerogs.cpp:3538: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:3545: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:3737: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:4064: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::SetTexVariables(int, FRAGMENTSHADER*, int)’:
zerogs.cpp:4649: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::SetTexVariablesInt(int, int, const tex0Info&, ZeroGS::CMemoryTarget*, FRAGMENTSHADER*, int)’:
zerogs.cpp:4852: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp:4870: warning: deprecated conversion from string constant to ‘char*’
zerogs.cpp: In function ‘void ZeroGS::StartCapture()’:
zerogs.cpp:5905: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroGSogl_a-zerogs.Tpo .deps/libZeroGSogl_a-zerogs.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I.  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer   -g -O2  -DZEROGS_SSE2 -MT libZeroGSogl_a-x86-32.o -MD -MP -MF .deps/libZeroGSogl_a-x86-32.Tpo -c -o libZeroGSogl_a-x86-32.o `test -f 'x86-32.S' || echo './'`x86-32.S
mv -f .deps/libZeroGSogl_a-x86-32.Tpo .deps/libZeroGSogl_a-x86-32.Po
rm -f libZeroGSogl.a
ar cru libZeroGSogl.a libZeroGSogl_a-GSmain.o libZeroGSogl_a-memcpy_amd.o libZeroGSogl_a-Regs.o libZeroGSogl_a-x86.o libZeroGSogl_a-zpipe.o libZeroGSogl_a-Mem.o libZeroGSogl_a-rasterfont.o libZeroGSogl_a-targets.o libZeroGSogl_a-zerogs.o  libZeroGSogl_a-x86-32.o 
ranlib libZeroGSogl.a
gcc  -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -shared -Wl,-soname,libZeroGSogl.so.0.96.2  -o libZeroGSoglr.so.0.96.2  libZeroGSogl_a-GSmain.o libZeroGSogl_a-memcpy_amd.o libZeroGSogl_a-Regs.o libZeroGSogl_a-x86.o libZeroGSogl_a-zpipe.o libZeroGSogl_a-Mem.o libZeroGSogl_a-rasterfont.o libZeroGSogl_a-targets.o libZeroGSogl_a-zerogs.o  libZeroGSogl_a-x86-32.o Linux/libZeroGSLinux.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lGL -lGLU -lGLEW -ljpeg -lpthread -lstdc++ -lz -ldl -lXxf86vm -lCg -lCgGL
make[2]: Entering directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/deten/pcsx2/bin/plugins" || /bin/mkdir -p "/home/deten/pcsx2/bin/plugins"
  /usr/bin/install -c 'libZeroGSoglr.so.0.96.2' '/home/deten/pcsx2/bin/plugins/libZeroGSoglr.so.0.96.2'
make[2]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
make[1]: Leaving directory `/home/deten/pcsx2/plugins/gs/zerogs/opengl'
------------------------
Building CDVD plugins...
------------------------
----------------
Building CDVDiso
----------------
rm -f libCDVDiso.so
gcc -shared -Wl,-soname,libCDVDiso.so -fPIC -Wall -g  -I.. -I. -D__LINUX__ -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   ../CDVDisop.o Config.o Linux.o ../libiso.o -o libCDVDiso.so -lz -lbz2 -lstdc++
rm -f cfgCDVDiso
gcc -fPIC -Wall -g  -I.. -I. -D__LINUX__ -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   conf.o interface.o support.o ../CDVDisop.o Config.o Linux.o ../libiso.o -o cfgCDVDiso -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lz -lbz2 -lstdc++
strip cfgCDVDiso
-------------------
Building CDVDisoEFP
-------------------
rm -f libCDVDisoEFP.so
gcc -shared -Wl,-soname,libCDVDisoEFP.so -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -lz -lbz2 \
	CDVDiso.o ../version.o actualfile.o ../isofile.o conf.o logfile.o ../imagetype.o ../multifile.o ../isocompress.o ../convert.o ../gzipv1.o ../blockv2.o ../gzipv2.o  ../ecma119.o ../bzip2v3.o ../bzip2v2.o ../toc.o ../ini.o -o libCDVDisoEFP.so
strip --strip-unneeded --strip-debug libCDVDisoEFP.so
rm -f cfgCDVDisoEFP
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -lz -lbz2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   \
	interface.o aboutbox.o mainbox.o selectionbox.o devicebox.o conversionbox.o progressbox.o messagebox.o tablerebuild.o device.o CD.o DVD.o ../version.o actualfile.o ../isofile.o conf.o logfile.o ../imagetype.o ../multifile.o ../isocompress.o ../convert.o ../gzipv1.o ../blockv2.o ../gzipv2.o  ../ecma119.o ../bzip2v3.o ../bzip2v2.o ../toc.o ../ini.o -o cfgCDVDisoEFP
strip cfgCDVDisoEFP
------------------
Building CDVDlinuz
------------------
gcc -shared -Wl,-soname,libCDVDlinuz.so -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux  \
	CDVDlinuz.o ../buffer.o actualfile.o conf.o logfile.o device.o CD.o DVD.o ../convert.o ../ini.o ../version.o -o libCDVDlinuz.so
strip --strip-unneeded --strip-debug libCDVDlinuz.so
gcc -fPIC -Wall -O2 -fomit-frame-pointer -D_LARGEFILE64_SOURCE -I.. -I. -I./Linux -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   \
	aboutbox.o mainbox.o interface.o actualfile.o conf.o logfile.o device.o CD.o DVD.o ../convert.o ../ini.o ../version.o -o cfgCDVDlinuz
strip cfgCDVDlinuz
-----------------
Building CDVDnull
-----------------
gcc -shared -Wl,-soname,libCDVDnull.so -Wall -O2 -fomit-frame-pointer -finline-functions -ffast-math -fno-strict-aliasing -I. -I/usr/local/include -DENABLE_NLS -DPACKAGE=\"pcsx2\" -fPIC CDVD.o -o libCDVDnull.so 
strip libCDVDnull.so
------------------------
Building DEV9 plugins...
------------------------
Building dev9null...
rm -f libDEV9null.so
gcc -shared -Wl,-soname,libDEV9null.so -fPIC -Wall -O2 -fomit-frame-pointer -D__LINUX__ dev9null.o -o libDEV9null.so 
strip --strip-unneeded --strip-debug libDEV9null.so
----------------------------
Building FireWire plugins...
----------------------------
---------------
Building FWnull
---------------
rm -f libFWnull.so
gcc -shared -Wl,-soname,libFWnull.so -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -D__LINUX__ ../FW.o Linux.o Config.o -o libFWnull.so -lpthread
strip --strip-unneeded --strip-debug libFWnull.so
rm -f cfgFWnull
gcc -fPIC -Wall -I. -I.. -O3 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -D__LINUX__ conf.o interface.o support.o Config.o -o cfgFWnull -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
strip cfgFWnull
-----------------------
Building PAD plugins...
-----------------------
----------------
Building ZeroPAD
----------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for a x86-64 CPU... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for SDL_Init in -lSDL... no
checking gtk2+... checking for pkg-config... pkg-config
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
Package sdl was not found in the pkg-config search path.
Perhaps you should add the directory containing `sdl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sdl' found
checking for main in -lstdc++... yes
checking for main in -ldl... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
Configuration:
  Debug build?	       no
  x86-64 build?	       no
test -z "libZeroPAD.a" || rm -f libZeroPAD.a
test -z "libZeroPAD.so.0.2.0" || rm -f libZeroPAD.so.0.2.0
rm -f *.o
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -I.    -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -O2 -fomit-frame-pointer   -MT libZeroPAD_a-zeropad.o -MD -MP -MF .deps/libZeroPAD_a-zeropad.Tpo -c -o libZeroPAD_a-zeropad.o `test -f 'zeropad.cpp' || echo './'`zeropad.cpp
zeropad.cpp:34: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘s32 PADinit(u32)’:
zeropad.cpp:168: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 PADstartPoll(int)’:
zeropad.cpp:251: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 _PADpoll(u8)’:
zeropad.cpp:265: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp:400: warning: deprecated conversion from string constant to ‘char*’
zeropad.cpp: In function ‘u8 PADpoll(u8)’:
zeropad.cpp:470: warning: deprecated conversion from string constant to ‘char*’
mv -f .deps/libZeroPAD_a-zeropad.Tpo .deps/libZeroPAD_a-zeropad.Po
gcc -DPACKAGE_NAME=\"ZeroPAD\" -DPACKAGE_TARNAME=\"zeropad\" -DPACKAGE_VERSION=\"0.2\" -DPACKAGE_STRING=\"ZeroPAD\ 0.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroPAD\" -DVERSION=\"0.2\" -DNDEBUG=1 -I.    -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1    -O2 -fomit-frame-pointer   -MT libZeroPAD_a-linux.o -MD -MP -MF .deps/libZeroPAD_a-linux.Tpo -c -o libZeroPAD_a-linux.o `test -f 'Linux/linux.cpp' || echo './'`Linux/linux.cpp
Linux/linux.cpp:25:21: error: SDL/SDL.h: No such file or directory
Linux/linux.cpp:71: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:71: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:74: error: expected `;' before ‘private’
Linux/linux.cpp:85: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
Linux/linux.cpp:85: error: expected ‘;’ before ‘*’ token
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp:120: warning: deprecated conversion from string constant to ‘char*’
Linux/linux.cpp: In function ‘void PADupdate(int)’:
Linux/linux.cpp:319: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:328: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:328: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:340: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:340: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp:388: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:388: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp: In function ‘void OnConf_Key(GtkButton*, void*)’:
Linux/linux.cpp:499: error: ‘SDL_JoystickUpdate’ was not declared in this scope
Linux/linux.cpp:525: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:525: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:542: error: ‘class JoystickInfo’ has no member named ‘GetJoy’
Linux/linux.cpp:542: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
Linux/linux.cpp: In static member function ‘static void JoystickInfo::EnumerateJoysticks(std::vector<JoystickInfo*, std::allocator<JoystickInfo*> >&)’:
Linux/linux.cpp:717: error: ‘SDL_INIT_JOYSTICK’ was not declared in this scope
Linux/linux.cpp:717: error: ‘SDL_Init’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_QUERY’ was not declared in this scope
Linux/linux.cpp:719: error: ‘SDL_JoystickEventState’ was not declared in this scope
Linux/linux.cpp:726: error: ‘SDL_NumJoysticks’ was not declared in this scope
Linux/linux.cpp: In constructor ‘JoystickInfo::JoystickInfo()’:
Linux/linux.cpp:753: error: ‘joy’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::Destroy()’:
Linux/linux.cpp:764: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:765: error: ‘SDL_JoystickOpened’ was not declared in this scope
Linux/linux.cpp:766: error: ‘SDL_JoystickClose’ was not declared in this scope
Linux/linux.cpp: In member function ‘bool JoystickInfo::Init(int, bool)’:
Linux/linux.cpp:778: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:778: error: ‘SDL_JoystickOpen’ was not declared in this scope
Linux/linux.cpp:784: error: ‘SDL_JoystickNumAxes’ was not declared in this scope
Linux/linux.cpp:785: error: ‘SDL_JoystickNumButtons’ was not declared in this scope
Linux/linux.cpp:786: error: ‘SDL_JoystickNumHats’ was not declared in this scope
Linux/linux.cpp:787: error: ‘SDL_JoystickName’ was not declared in this scope
Linux/linux.cpp: In member function ‘void JoystickInfo::SaveState()’:
Linux/linux.cpp:821: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:821: error: ‘SDL_JoystickGetButton’ was not declared in this scope
Linux/linux.cpp:823: error: ‘joy’ was not declared in this scope
Linux/linux.cpp:823: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
make: *** [libZeroPAD_a-linux.o] Error 1
Error with building plugins
deten@deten-laptop:~/pcsx2$ 

```

---

### Post by lubosz on 2008-09-12
the important error in your post is:
error: SDL/SDL.h: No such file or directory

get SDL headers (sdl dev packages), and it should work.
libsdl1.2-dev (in intrepid, not in hardy right now, but there should be a similar)

did you read the INSTALL file? how did you install the nvidia C for Graphics SDK? I try to install it right now with alien

---

