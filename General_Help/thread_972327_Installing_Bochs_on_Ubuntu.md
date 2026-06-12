---
title: "Installing Bochs on Ubuntu"
date: 2008-11-05
forum: General Help
---

### Post by cjjoy1980 on 2008-11-05
Hi,
I am installing Bochs on 32 bit cpu with U-buntu OS.  I am getting the following error when running the make command.  Please let me know if I am missing any supporting packages or configuration options. 
  
make 
cd iodev && \ 
        make  libiodev.a 
make[1]: Entering directory `/pintos/bochs-2.3.7/iodev' 
g++ -c  -I.. -I./.. -I../instrument/stubs -I./../instrument/stubs -g -O2 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES    devices.cpp -o devices.o 
In file included from ../bochs.h:37, 
                 from devices.cpp:32: 
../config.h:795:2: error: #error "Page Global Extension (PGE) only supported with CPU_LEVEL >= 6 !" 
make[1]: *** [devices.o] Error 1 
make[1]: Leaving directory `/pintos/bochs-2.3.7/iodev' 
make: *** [iodev/libiodev.a] Error 2 

I have enabled the following options while running the configure script: 
 ./configure --enable-plugins --enable-usb  --enable-global-pages --enable-fast-function-calls --enable-host-specific-asms --enable-cpp --enable-debugger --enable-disasm --enable-readline --enable-logging --enable-raw-serial --enable-fpu --enable-vme --enable-x86-debugger  --enable-pci --with-x --with-x11 --with-term --with-nogui 

Configure output: 
---------------------- 
checking build system type... i686-pc-linux-gnu 
checking host system type... i686-pc-linux-gnu 
checking target system type... i686-pc-linux-gnu 
checking if you are configuring for another platform... no 
checking for standard CFLAGS on this platform... 
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
checking whether make sets $(MAKE)... yes 
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
checking how to run the C++ preprocessor... g++ -E 
checking for g77... no 
checking for f77... no 
checking for xlf... no 
checking for frt... no 
checking for pgf77... no 
checking for cf77... no 
checking for fort77... no 
checking for fl32... no 
checking for af77... no 
checking for f90... no 
checking for xlf90... no 
checking for pgf90... no 
checking for pghpf... no 
checking for epcf90... no 
checking for gfortran... no 
checking for g95... no 
checking for f95... no 
checking for fort... no 
checking for xlf95... no 
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
checking for shl_load... no 
checking for shl_load in -ldld... no 
checking for dlopen... no 
checking for dlopen in -ldl... yes 
checking whether a program can dlopen itself... yes 
checking whether a statically linked program can dlopen itself... yes 
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
checking if g++ supports -c -o file.o... yes 
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking for shl_load... (cached) no 
checking for shl_load in -ldld... (cached) no 
checking for dlopen... (cached) no 
checking for dlopen in -ldl... (cached) yes 
checking whether a program can dlopen itself... (cached) yes 
checking whether a statically linked program can dlopen itself... (cached) yes 
appending configuration tag "F77" to libtool 
checking for an ANSI C-conforming const... yes 
checking for dirent.h that defines DIR... yes 
checking for library containing opendir... none required 
checking which extension is used for loadable modules... .so 
checking which variable specifies run-time library path... LD_LIBRARY_PATH 
checking for the default library search path... /lib /usr/lib 
checking for objdir... .libs 
checking whether libtool supports -dlopen/-dlpreopen... yes 
checking for shl_load... (cached) no 
checking for shl_load in -ldld... (cached) no 
checking for dlopen in -ldl... (cached) yes 
checking for dlerror... yes 
checking for _ prefix in compiled symbols... no 
checking whether deplibs are loaded by dlopen... yes 
checking argz.h usability... yes 
checking argz.h presence... yes 
checking for argz.h... yes 
checking for error_t... yes 
checking for argz_append... yes 
checking for argz_create_sep... yes 
checking for argz_insert... yes 
checking for argz_next... yes 
checking for argz_stringify... yes 
checking assert.h usability... yes 
checking assert.h presence... yes 
checking for assert.h... yes 
checking ctype.h usability... yes 
checking ctype.h presence... yes 
checking for ctype.h... yes 
checking errno.h usability... yes 
checking errno.h presence... yes 
checking for errno.h... yes 
checking malloc.h usability... yes 
checking malloc.h presence... yes 
checking for malloc.h... yes 
checking for memory.h... (cached) yes 
checking for stdlib.h... (cached) yes 
checking stdio.h usability... yes 
checking stdio.h presence... yes 
checking for stdio.h... yes 
checking for unistd.h... (cached) yes 
checking dl.h usability... no 
checking dl.h presence... no 
checking for dl.h... no 
checking sys/dl.h usability... no 
checking sys/dl.h presence... no 
checking for sys/dl.h... no 
checking dld.h usability... no 
checking dld.h presence... no 
checking for dld.h... no 
checking mach-o/dyld.h usability... no 
checking mach-o/dyld.h presence... no 
checking for mach-o/dyld.h... no 
checking for string.h... (cached) yes 
checking for strchr... yes 
checking for strrchr... yes 
checking for memcpy... yes 
checking for memmove... yes 
checking for strcmp... yes 
checking for closedir... yes 
checking for opendir... yes 
checking for readdir... yes 
checking for X... libraries , headers 
checking for gethostbyname... yes 
checking for connect... yes 
checking for remove... yes 
checking for shmat... yes 
checking for IceConnectionNumber in -lICE... yes 
checking whether byte ordering is bigendian... no 
checking for inline... inline 
checking for unsigned char... yes 
checking size of unsigned char... 1 
checking for unsigned short... yes 
checking size of unsigned short... 2 
checking for unsigned int... yes 
checking size of unsigned int... 4 
checking for unsigned long... yes 
checking size of unsigned long... 4 
checking for unsigned long long... yes 
checking size of unsigned long long... 8 
checking for int *... yes 
checking size of int *... 4 
checking for getenv... yes 
checking for setenv... yes 
checking for select... yes 
checking for snprintf... yes 
checking for vsnprintf... yes 
checking for strtoull... yes 
checking for strtouq... yes 
checking for strdup... yes 
checking for strrev... no 
checking for sleep... yes 
checking for usleep... yes 
checking for nanosleep... yes 
checking for abort... yes 
checking for gettimeofday... yes 
checking for socklen_t... yes 
checking for struct sockaddr_in.sin_len... no 
checking for mkstemp... yes 
checking sys/mman.h usability... yes 
checking sys/mman.h presence... yes 
checking for sys/mman.h... yes 
checking for timelocal... yes 
checking for gmtime... yes 
checking for mktime... yes 
checking for _FILE_OFFSET_BITS value needed for large files... 64 
checking if large file support is available... yes 
checking for cos... no 
checking for floor... no 
checking if math functions link without -lm... no 
checking for sin... yes 
checking for ceil... yes 
checking if math functions link with -lm... yes 
checking for struct timeval... yes 
checking if compiler allows empty structs... yes 
checking if compiler allows __attribute__... yes 
checking for hash_map... no 
checking for hash_map.h... yes 
checking for set... yes 
checking for set.h... yes 
checking for idle hack... no 
checking for dlfcn.h... (cached) yes 
checking for assert.h... (cached) yes 
checking for plugins support... yes 
checking if compiler allows blank labels... no 
checking if compiler allows LL for 64-bit constants... yes 
checking for x86-64 support... no 
checking for SMP support... no 
checking for cpu level... 5 
checking for APIC support... no 
checking zlib.h usability... no 
checking zlib.h presence... no 
checking for zlib.h... no 
checking for compressed hard disk image support... no 
checking for NE2000 support... no 
checking for ACPI support... no 
checking for i440FX PCI support... yes 
checking for PCI host device mapping support... no 
checking for limited USB support... yes 
checking for PCI pseudo NIC support... no 
checking for large pages support... yes 
checking for PAE support... no 
checking for global pages support... yes 
checking for MTRRs support... no 
checking for guest to host TLB support... no 
checking for repeated IO and mem copy speedups... no 
checking for instruction trace cache support... no 
checking for instruction cache support... no 
checking for gcc fast function calls optimization... yes 
checking for host specific inline assembly accelerations... yes 
checking whether to ignore bad MSR references... yes 
checking for port e9 hack... yes 
checking show IPS... no 
checking for use of .cpp as suffix... yes 
moving .cc source files to .cpp 
no more .cc source files to rename 
checking for Bochs internal debugger support... yes 
checking for external debugger... no 
checking for disassembler support... yes 
checking for ALL optimizations enabled... no 
checking whether user wants readline... yes 
checking whether to use readline... checking if readline works without -lcurses... no 
checking if readline works with -lcurses... no 
no 
WARNING: The readline library was disabled because it was not found. 
checking readline/history.h usability... no 
checking readline/history.h presence... no 
checking for readline/history.h... no 
checking for instrumentation support... no 
checking enable logging... yes 
checking for raw serial support... yes 
checking for VESA BIOS extensions... yes 
checking for CLGD54XX emulation... no 
checking for FPU emulation... yes 
checking for VME support... yes 
checking for MMX support... yes 
checking for 3DNow! support... no 
checking for SSE support... no 
checking for SSE extensions support... no 
checking for DAZ support... no 
checking for XSAVE/XRSTOR support... no 
checking for AES instructions support... no 
checking for alignment check support... yes 
checking for misaligned SSE support... no 
checking for SEP support... no 
checking for POPCNT instruction support... no 
checking for MONITOR/MWAIT instructions support (experimental)... no 
checking for x86 debugger support... yes 
checking IOKit/storage/IOCDMedia.h usability... no 
checking IOKit/storage/IOCDMedia.h presence... no 
checking for IOKit/storage/IOCDMedia.h... no 
checking for CDROM support... yes 
checking for Sound Blaster 16 support... no 
checking for standard PC gameport support... no 
checking for gdb stub enable... no 
checking for I/O Interface to the debugger... no 
checking for docbook2html... not_found 
checking whether to build docbook documentation... no 
checking for wx-config... wx-config 
checking for wxWidgets configuration script... wx-config 
checking for wxWidgets library version... 2.6.3 
checking for default gui on this platform... x11 
checking whether user wants XPM support... yes 
checking X11/xpm.h usability... no 
checking X11/xpm.h presence... no 
checking for X11/xpm.h... no 
checking for display libraries...  X11 term nogui 
checking for wget... wget 
checking for mvaddch in -lcurses... yes 
checking for mvaddch in -lncurses... yes 
checking for mvaddch in -ltermlib... no 
checking for mvaddch in -lpdcurses... no 
checking for color_set... yes 
checking for mvhline... yes 
checking for mvvline... yes 
checking pthread.h usability... yes 
checking pthread.h presence... yes 
checking for pthread.h... yes 
checking for the pthreads library -lpthreads... no 
checking whether pthreads work without any flags... no 
checking whether pthreads work with -Kthread... no 
checking whether pthreads work with -kthread... no 
checking for the pthreads library -llthread... no 
checking whether pthreads work with -pthread... yes 
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE 
checking if more special flags are required for pthreads... no 
checking for cc_r... gcc 
checking for magic breakpoints (deprecated)... no 
checking for save/restore (deprecated)... no 
checking for gzip... /bin/gzip 
checking for tar... /bin/tar 
configure: creating ./config.status 
config.status: creating Makefile 
config.status: creating iodev/Makefile 
config.status: creating bx_debug/Makefile 
config.status: creating bios/Makefile 
config.status: creating cpu/Makefile 
config.status: creating memory/Makefile 
config.status: creating gui/Makefile 
config.status: creating disasm/Makefile 
config.status: creating instrument/stubs/Makefile 
config.status: creating misc/Makefile 
config.status: creating fpu/Makefile 
config.status: creating doc/docbook/Makefile 
config.status: creating build/linux/bochs-dlx 
config.status: creating bxversion.h 
config.status: creating bxversion.rc 
config.status: creating build/macosx/Info.plist 
config.status: creating build/win32/nsis/Makefile 
config.status: creating build/win32/nsis/bochs.nsi 
config.status: creating host/linux/pcidev/Makefile 
config.status: creating config.h 
config.status: creating ltdlconf.h 
config.status: ltdlconf.h is unchanged

---

### Post by mcantaluppi on 2011-04-13
Hi, Did you finally solve it? I'm having the same problem trying to compiling bochs:

The readline library was disabled because it was not found.

I'm using this sentence for config:

./configure --enable-debugger --enable-disasm --prefix=/opt/bochs-2.4.6.1 --enable-fpu --enable-configurable-msrs --enable-cpu-level=6 --enable-pci --enable-usb

If anyone can help me it will be great. Thank you everybody.

---

