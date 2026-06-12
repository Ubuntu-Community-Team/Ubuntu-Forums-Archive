---
title: "wacom bamboo fun &amp; touch - problems"
date: 2009-12-19
forum: Hardware
---

### Post by nocentis on 2009-12-19
Hello  installed and I have a problem with talbetem wacom bamboo ...
Downloaded the drivers and the installation of my message pops up:
```
mab@mab-laptop:~/Desktop/linuxwacom-0.8.4-4$ sudo ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gawk... (cached) mawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking the maximum length of command line arguments... 1572864
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.28-13-generic/build
checking kernel version... 2.6.28-13-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Uninit is called... yes
checking if Xorg is version 1.6 or later... yes
yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for XORG... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/2.6.28/Makefile
config.status: creating src/2.6.31/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.28
  module versioning - no 
      kernel source - yes /lib/modules/2.6.28-13-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
Making all in src
make[1]: Entering directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src'
Making all in .
make[2]: Entering directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src'
Making all in wacomxi
make[2]: Entering directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
wacomxi.c:1850: fatal error: opening dependency file .deps/wacomxi.Tpo: Permission denied
compilation terminated.
make[2]: *** [wacomxi.lo] Error 1
make[2]: Leaving directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src/wacomxi'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mab/Desktop/linuxwacom-0.8.4-4/src'
make: *** [all-recursive] Error 1
mab@mab-laptop:~/Desktop/linuxwacom-0.8.4-4$ 

```How to fix?

---

### Post by Ayuthia on 2009-12-19
> **nocentis said:**
> Hello  installed and I have a problem with talbetem wacom bamboo ...
Downloaded the drivers and the installation of my message pops up:
```
mab@mab-laptop:~/Desktop/linuxwacom-0.8.4-4$ sudo ./configure && make

```
The ./configure and make do not require sudo privileges.  The reason for the error is because you did the configure using sudo so it prevented the make to access the Makefile.

However, you have the Fun and Touch version so this version of linuxwacom does not support your device.  We have created a working version at this post:
[http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

Hope that helps.

---

