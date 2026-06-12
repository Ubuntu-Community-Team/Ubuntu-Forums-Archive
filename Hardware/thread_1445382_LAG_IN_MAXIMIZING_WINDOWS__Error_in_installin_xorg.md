---
title: "LAG IN MAXIMIZING WINDOWS / Error in installin xorg-server-1.6.4"
date: 2010-04-02
forum: Hardware
---

### Post by asn_knight on 2010-04-02
Ok...Long story!
I installed Ubuntu to find that it doesnt support my ATI Mob.Radeon 3460 too well.
I tried on the internet and found a guy who solved his problem well :
[http://blog.desair-homble.be/#post50](http://blog.desair-homble.be/#post50)
Well I did as he told...and installed the hard disk.
The .run file whic was showing some error now installed well (or is it?)
Then I noticed a problem. The same one like in the blog.
DELAY IN MINIMIZING AND MAXIMIZING OF WINDOWS.

Again, wonderfully Tom already had faced by the same prob.
Like he tells in his blog he told me to add the PPA. I did.
I downloaded the tar.gz file. Extracted it.
BUt when I gav './configure' It gav the following output.
```
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
checking dependency style of gcc... gcc3
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for flex... no
checking for lex... no
checking for bison... no
checking for byacc... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for cpp... /usr/bin/cpp
checking if /usr/bin/cpp requires -undef... yes
checking if /usr/bin/cpp requires -traditional... yes
checking for sed... (cached) /bin/sed
checking for dtrace... not_found
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... no
checking size of unsigned long... 4
checking for pid_t... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking sys/endian.h usability... no
checking sys/endian.h presence... no
checking for sys/endian.h... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for vprintf... yes
checking for _doprnt... no
checking for geteuid... yes
checking for getuid... yes
checking for link... yes
checking for memmove... yes
checking for memset... yes
checking for mkstemp... yes
checking for strchr... yes
checking for strrchr... yes
checking for strtol... yes
checking for getopt... yes
checking for getopt_long... yes
checking for vsnprintf... yes
checking for walkcontext... no
checking for backtrace... yes
checking for getisax... no
checking for getzoneid... no
checking for shmctl64... no
checking for strcasestr... yes
checking for ffs... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for getdtablesize... yes
checking for getifaddrs... yes
checking for getpeereid... no
checking for getpeerucred... no
checking for strlcat... no
checking for strlcpy... no
checking for mmap... yes
checking for sqrt in -lm... yes
checking for cbrt in -lm... yes
checking ndbm.h usability... no
checking ndbm.h presence... no
checking for ndbm.h... no
checking dbm.h usability... no
checking dbm.h presence... no
checking for dbm.h... no
checking rpcsvc/dbm.h usability... no
checking rpcsvc/dbm.h presence... no
checking for rpcsvc/dbm.h... no
checking linux/agpgart.h usability... yes
checking linux/agpgart.h presence... yes
checking for linux/agpgart.h... yes
checking sys/agpio.h usability... no
checking sys/agpio.h presence... no
checking for sys/agpio.h... no
checking linux/apm_bios.h usability... yes
checking linux/apm_bios.h presence... yes
checking for linux/apm_bios.h... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking asm/mtrr.h usability... yes
checking asm/mtrr.h presence... yes
checking for asm/mtrr.h... yes
checking sys/memrange.h usability... no
checking sys/memrange.h presence... no
checking for sys/memrange.h... no
checking machine/mtrr.h usability... no
checking machine/mtrr.h presence... no
checking for machine/mtrr.h... no
checking for sys/linker.h... no
checking for SYSV IPC... yes
checking machine/apmvar.h usability... no
checking machine/apmvar.h presence... no
checking for machine/apmvar.h... no
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking for backtrace in -lc... yes
checking to see if we can install the Xorg server as root... no
checking if Xtrans should support UNIX socket connections... yes
checking if Xtrans should support TCP socket connections... yes
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for main in -lws2_32... no
checking for getaddrinfo... yes
checking if IPv6 support should be built... yes
./configure: line 15287: ac_fn_c_check_member: command not found
checking for socklen_t... yes
checking if Xtrans should support os-specific local connections... no
checking for authdes_seccreate... no
checking for authdes_create... yes
checking for library containing getsecretkey... none required
checking if Secure RPC authentication ("SUN-DES-1") should be supported... yes
checking for NONE/share/sgml/X11/defs.ent... no
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
checking Whether to build documentation... no
checking Whether to build pdf documentation... yes
checking for DBUS... no
checking for HAL... no
checking for glibc...... yes
checking for clock_gettime... no
checking for clock_gettime in -lrt... yes
checking for a useful monotonic clock ...... yes
checking for XLIB... configure: error: Package requirements (x11) were not met:

No package 'x11' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XLIB_CFLAGS
and XLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```And 'make' and 'make install' commands didnt work.

Hav any solution to make this work OR hav any other solution fr the lag in minimizing 
and maximizing of windows?

---

### Post by asn_knight on 2010-04-03
Well I didnt get any solution for the errors of ./configure command.
But got a woraround for removing the LAG!!!
Cool! After searchin since 4-5 months and reinstallin for 2-3 tmes coz of this bug.
Check the last but 1 post  of 
[http://ubuntuforums.org/archive/index.php/t-1107559.html](http://ubuntuforums.org/archive/index.php/t-1107559.html)
Thanks @radec!! U r my saviour!

Enjoy,
--asn_knight--

---

