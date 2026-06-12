---
title: "need help to compile intel graphics drivers"
date: 2011-07-05
forum: Hardware
---

### Post by ecefadi on 2011-07-05
[SIZE=4][COLOR=Red]hi folks 
[/COLOR][/SIZE][SIZE=4][COLOR=Red]i need help to install driver for backtrack 4 r2 for intel graphics hd graphics 

i have done ./configure command [/COLOR][/SIZE]

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... no, using cp -p
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... no
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
checking if g++ static flag -static works... no
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for intel-gen4asm... no
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for PCIACCESS... yes
checking for ANSI C header files... (cached) yes
checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for xf86Modes.h... yes
built-in mode code
checking for DRI... yes
checking for DRI_MM... yes
checking for NONE/share/X11/sgml/defs.ent... no
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
checking Whether to build documentation... no
checking Whether to build pdf documentation... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating src/bios_reader/Makefile
config.status: creating src/ch7017/Makefile
config.status: creating src/ch7xxx/Makefile
config.status: creating src/ivch/Makefile
config.status: creating src/reg_dumper/Makefile
config.status: creating src/sil164/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@bt:/mnt/flash/xf86-video-intel-1.9.91#




[SIZE=4][COLOR=Red]and i tried make install and that what happens[/COLOR][/SIZE]


make install
Making install in src
make[1]: Entering directory `/mnt/flash/xf86-video-intel-1.9.91/src'
Making install in xvmc
make[2]: Entering directory `/mnt/flash/xf86-video-intel-1.9.91/src/xvmc'
make[3]: Entering directory `/mnt/flash/xf86-video-intel-1.9.91/src/xvmc'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../../libtool --mode=install /usr/bin/install -c  'libI810XvMC.la' '/usr/local/lib/libI810XvMC.la'
/usr/bin/install -c .libs/libI810XvMC.so.1.0.0 /usr/local/lib/libI810XvMC.so.1.0.0
(cd /usr/local/lib && { cp -p -f libI810XvMC.so.1.0.0 libI810XvMC.so.1 || { rm -f libI810XvMC.so.1 && cp -p libI810XvMC.so.1.0.0 libI810XvMC.so.1; }; })
(cd /usr/local/lib && { cp -p -f libI810XvMC.so.1.0.0 libI810XvMC.so || { rm -f libI810XvMC.so && cp -p libI810XvMC.so.1.0.0 libI810XvMC.so; }; })
/usr/bin/install -c .libs/libI810XvMC.lai /usr/local/lib/libI810XvMC.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
/sbin/ldconfig.real: /usr/local/lib/libI810XvMC.so.1 is not a symbolic link

----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/mnt/flash/xf86-video-intel-1.9.91/src/xvmc'
make[2]: Leaving directory `/mnt/flash/xf86-video-intel-1.9.91/src/xvmc'
Making install in bios_reader
make[2]: Entering directory `/mnt/flash/xf86-video-intel-1.9.91/src/bios_reader'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -I/usr/include/xorg -I/usr/include/pixman-1    -g -O2 -MT bios_reader.o -MD -MP -MF ".deps/bios_reader.Tpo" -c -o bios_reader.o bios_reader.c; \
        then mv -f ".deps/bios_reader.Tpo" ".deps/bios_reader.Po"; else rm -f ".deps/bios_reader.Tpo"; exit 1; fi
In file included from bios_reader.c:34:
/usr/include/xorg/edid.h:439: error: expected specifier-qualifier-list before 'CARD16'
In file included from bios_reader.c:41:
../i830_bios.h:30: error: expected specifier-qualifier-list before 'CARD16'
../i830_bios.h:44: error: expected specifier-qualifier-list before 'CARD16'
../i830_bios.h:57: error: expected specifier-qualifier-list before 'CARD8'
../i830_bios.h:65: error: expected specifier-qualifier-list before 'CARD16'
../i830_bios.h:81: error: expected specifier-qualifier-list before 'CARD16'
../i830_bios.h:103: error: expected specifier-qualifier-list before 'CARD16'
../i830_bios.h:112: error: expected specifier-qualifier-list before 'CARD8'
bios_reader.c:46: error: expected specifier-qualifier-list before 'CARD8'
bios_reader.c: In function 'main':
bios_reader.c:78: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:79: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:82: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:82: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:84: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:86: error: 'struct vbt_header' has no member named 'version'
bios_reader.c:86: error: 'struct vbt_header' has no member named 'version'
bios_reader.c:88: error: 'struct vbt_header' has no member named 'bdb_offset'
bios_reader.c:89: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:91: error: 'struct bdb_header' has no member named 'version'
bios_reader.c:91: error: 'struct bdb_header' has no member named 'version'
bios_reader.c:92: error: 'struct bdb_header' has no member named 'header_size'
bios_reader.c:92: error: 'struct bdb_header' has no member named 'bdb_size'
bios_reader.c:101: error: 'CARD8' undeclared (first use in this function)
bios_reader.c:101: error: (Each undeclared identifier is reported only once
bios_reader.c:101: error: for each function it appears in.)
bios_reader.c:101: error: 'timing_ptr' undeclared (first use in this function)
bios_reader.c:103: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:104: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:104: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:108: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:109: error: 'struct lvds_bdb_1' has no member named 'panel_type'
bios_reader.c:110: error: 'struct lvds_bdb_1' has no member named 'caps'
bios_reader.c:118: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:120: error: 'struct lvds_bdb_2' has no member named 'table_size'
bios_reader.c:123: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:124: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:125: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:126: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:127: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:128: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:129: error: 'struct lvds_bdb_2_fp_params' has no member named 'terminator'
bios_reader.c:133: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:134: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:135: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:136: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:137: error: 'struct _fake_i830' has no member named 'VBIOS'
bios_reader.c:138: error: 'struct lvds_bdb_2' has no member named 'panels'
bios_reader.c:140: error: 'struct lvds_bdb_2_fp_params' has no member named 'terminator'
bios_reader.c:148: error: 'struct lvds_bdb_2_fp_params' has no member named 'x_res'
bios_reader.c:148: error: 'struct lvds_bdb_2_fp_params' has no member named 'y_res'
bios_reader.c:157: error: 'struct lvds_bdb_2_fp_params' has no member named 'x_res'
bios_reader.c:157: error: 'struct lvds_bdb_2_fp_params' has no member named 'y_res'
make[2]: *** [bios_reader.o] Error 1
make[2]: Leaving directory `/mnt/flash/xf86-video-intel-1.9.91/src/bios_reader'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/mnt/flash/xf86-video-intel-1.9.91/src'
make: *** [install-recursive] Error 1
root@bt:/mnt/flash/xf86-video-intel-1.9.91#      



[SIZE=4][COLOR=Red]and this is the ls output [/COLOR][/SIZE]


/mnt/flash/xf86-video-intel-1.9.91# ls
COPYING    Makefile.am  README.sgml  compile       config.h.in    config.sub    depcomp     ltmain.sh  src
ChangeLog  Makefile.in  TODO         config.guess  config.log     configure     install-sh  man        stamp-h1
Makefile   README       aclocal.m4   config.h      config.status  configure.ac  libtool     missing
root@bt:/mnt/flash/xf86-video-intel-1.9.91#

---

