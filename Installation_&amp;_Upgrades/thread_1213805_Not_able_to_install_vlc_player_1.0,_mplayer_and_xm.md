---
title: "Not able to install vlc player 1.0, mplayer and xmms-1.2.11 in ubuntu 9.04"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by sskrajak on 2009-07-15
I am new to ubuntu world.I have ubuntu 9.04, which is upgraded drom 8.04 to 8.10 and then 8.10 to 9.04. in between these upgrades no other application was installed in any way.
  I do not have internet connection.


Now i am trying to install vlc-1.0.0 ,gnome-mplayer-0.9.6 and xmms-1.2.11 in the version 9.04. All these are failing in one way or other.

for gnome-mplayer-0.9.6 . while doing ./configure i got below message

shashikant@shashikant-desktop:~/Desktop/gnome-mplayer-0.9.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for msgfmt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


for vlc-1.0.0 . while doing ./configure i got below message
shashikant@shashikant-desktop:~/Desktop/vlc-1.0.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for egrep... (cached) /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking dependency style of gcc -std=gnu99... gcc3
checking for ranlib... ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for dlltool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for libs in /home/shashikant/Desktop/vlc-1.0.0/./extras/contrib... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc -std=gnu99... ld
checking if the linker (ld) is GNU ld... yes
checking for ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... (cached) pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for objdir... .libs
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC
checking if gcc -std=gnu99 PIC flag -fPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking whether the gcc -std=gnu99 linker (ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... ld
checking if the linker (ld) is GNU ld... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... ld
checking if the linker (ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking for gettimeofday... yes
checking for isatty... yes
checking for sigrelse... yes
checking for getpwuid_r... yes
checking for memalign... yes
checking for posix_memalign... yes
checking for if_nametoindex... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking for ctime_r... yes
checking for lrintf... no
checking for daemon... yes
checking for fork... yes
checking for lstat... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for uselocale... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for fcntl... yes
checking for asprintf... yes
checking for atof... yes
checking for atoll... yes
checking for getcwd... yes
checking for gmtime_r... yes
checking for lldiv... yes
checking for localtime_r... yes
checking for rewind... yes
checking for strcasecmp... yes
checking for strcasestr... yes
checking for strdup... yes
checking for strlcpy... no
checking for strncasecmp... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtof... yes
checking for strtoll... yes
checking for vasprintf... yes
checking for swab... yes
checking for stricmp... no
checking for strnicmp... no
checking for fdatasync... yes
checking for vmsplice... yes
checking for mmap... yes
checking for setlocale... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for nl_langinfo... yes
checking for nl_langinfo and CODESET... yes
checking for connect... yes
checking for send... yes
checking for socklen_t in sys/socket.h... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for getnameinfo... yes
checking for gai_strerror... yes
checking for struct addrinfo... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for inet_aton... yes
checking for getopt_long... yes
checking return type of signal handlers... void
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for exp in -lm... yes
checking for round in -lm... yes
checking for sqrtf in -lmx... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking for dld_link in -ldld... no
checking image.h usability... no
checking image.h presence... no
checking for image.h... no
checking for load_add_on... no
checking for dlfcn.h... (cached) yes
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for main in -lpthread... yes
checking for clock_nanosleep in -lrt... yes
checking for nanosleep... yes
checking for strncasecmp in strings.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for sys/types.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/udplite.h usability... no
checking netinet/udplite.h presence... no
checking for netinet/udplite.h... no
checking sys/eventfd.h usability... yes
checking sys/eventfd.h presence... yes
checking for sys/eventfd.h... yes
checking for net/if.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for ssize_t... yes
checking for library containing poll... none required
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for nanosleep in time.h... yes
checking for timespec in sys/time.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for HAL... no
configure: WARNING: libhal >= 0.5.0 was not found. Install libhal-dev ?
checking for MTP... no
configure: WARNING: MTP library not found
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?





for xmms-1.2.11 . while doing ./configure i got below message
shashikant@shashikant-desktop:~/Desktop/xmms-1.2.11$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
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
checking for strerror in -lcposix... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking whether assembler supports --noexecstack option... 	.section	.note.GNU-stack,"",@progbits
yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***


please tell how to install them from source.

i also tried the .deb packages for vlc and mplayer. It is also failing since many dependencies are not install.

---

### Post by Partyboi2 on 2009-07-16
Hi, its easier to install the deb packages then trying to compile. When you install the deb package and require other packages to met the dependencies you can find them [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") and download and install which can take awhile. Another option is to use [[COLOR=Blue]Keyrx[/COLOR]]("http://keryxproject.org/") which is a program for those who don't have Internet connection. You can also check its tutorial out [[COLOR=Blue]here[/COLOR]]("http://crashsystems.net/2009/01/keryx-tutorial/").

---

### Post by csabo2 on 2009-07-16
Look for things like this in all that mess


No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

You dont have the required packages to install these things. your best bet is to copy/paste them into a text file, print or save it, goto a machine with a connection and get all thoes files.

---

### Post by sskrajak on 2009-07-18
Already have taken 70 packages  from internet and have installed them in the 9.04 but still

mplayer_1.0~rc2-0ubuntu19_i386.deb installation is giving -----  Error: Dependency is not satisfiable: libenca0 (>= 1.9).

vlc-dbg_0.9.9a-2ubuntu1_i386.deb  installation is giving------  Error: Dependency is not satisfiable: vlc-nox (= 0.9.9a-2ubuntu1)

vlc-nox_0.9.9a-2ubuntu1_i386.deb installation is giving----- Error: Dependency is not satisfiable: libass1 

and so on............

I do not know have many 100's of dependencies is still pending to be get installed.

---

### Post by Partyboi2 on 2009-07-18
As I previously mentioned you can use Keryx to install the packages you want and all dependencies without having to manually install each one.

---

