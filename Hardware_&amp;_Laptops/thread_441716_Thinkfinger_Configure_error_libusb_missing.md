---
title: "Thinkfinger Configure: error: libusb missing"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by amhirsch on 2007-05-12
I'm trying to get thinkfinger installed on my T60 laptop in order to utilize bioapi as a login schema.  I'm getting the following error when I run configure:

/thinkfinger-0.3# ./configure --with-securedir=/lib/security --enable-pam --with-birdir=dir=/etc/pam_thinkfinger --prefix=/usr
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
checking for a BSD-compatible install... /usr/bin/install -c
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
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether gcc and cc understand -c and -o together... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking whether to build with USB hooks for debugging... no
checking whether to build the pluggable authentication module (PAM)... yes
checking security/pam_appl.h usability... yes
checking security/pam_appl.h presence... yes
checking for security/pam_appl.h... yes
checking security/pam_modules.h usability... yes
checking security/pam_modules.h presence... yes
checking for security/pam_modules.h... yes
checking for pam_start in -lpam... yes
checking for pam_prompt in -lpam... no
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking for linux/uinput.h... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... no
checking for USB... configure: error: libusb missing

Here are the usb related packages I have loaded:

/thinkfinger-0.3# dpkg --list | grep usb
ii  libusb++-0.1-4c2                           0.1.12-2                               userspace C++ USB programming library
ii  libusb++-dev                               0.1.12-2                               userspace C++ USB programming library develo
ii  libusb-0.1-4                               0.1.12-2                               userspace USB programming library
ii  libusb-dev                                 0.1.12-2                               userspace USB programming library developmen
ii  usbutils                                   0.72-7ubuntu2                          USB console utilities
ii  xserver-xorg-video-sisusb

I've been looking around but am shooting blanks, does anyone have any idea of what I am missing or where to look?

TIA!

---

### Post by amhirsch on 2007-05-12
I checked in my ld.so.cache to ensure I found references to libusb and here's what I found:

/etc# strings ld.so.cache | grep libusb
libusbpp-0.1.so.4
/usr/lib/libusbpp-0.1.so.4
libusb-0.1.so.4
/lib/libusb-0.1.so.4
libusb-0.1.so.4
/usr/lib/libusb-0.1.so.4

Note that I have tried to configure thinkfinger 0.3 & 0.2.2 and get the same error.

---

### Post by amhirsch on 2007-05-12
Oh ya, I'm running into this issue on a fresh install of Feisty (7.04).  Everything else seems to be working like a charm though! :)

TAIA!

---

### Post by amhirsch on 2007-05-14
Found the issue...be sure that you have pkg-config installed.  I did this and the package compiled successfully.  Hope this helps others! :KS

---

