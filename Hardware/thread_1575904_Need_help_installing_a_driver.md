---
title: "Need help installing a driver"
date: 2010-09-16
forum: Hardware
---

### Post by Radissthor on 2010-09-16
Hello Everyone,

I'm trying to install a driver in a Lunux Inspiron 11z to get my HDMI-to-VGA adapter working. I downloaded the manufacturer's driver (Linux Version), untared it and followed instructions in the read me file. Instructions were to run:
```

  $ ./configure
  $ sudo make install
  $ make check
```

from the folder where the file had been untared. The first two commands seemed to work good, but the last one didn't...

This is the output for ./configure:

```
natalia@Inspiron11z:~/Downloads/libdlo-0.1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
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
checking whether to build static libraries... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for inline... inline
checking for int32_t... yes
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for usb_open in -lusb... yes
checking for usb_get_driver_np... yes
checking for usb_get_configuration... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for gettimeofday... yes
checking for strchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating test/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

	libdlo 0.1.2
	========

	prefix:			/usr/local
	exec_prefix:		${prefix}
	libdir_name:		${exec_prefix}/lib
	mandir:			${datarootdir}/man
	includedir:		${prefix}/include

	compiler:		gcc
	cflags:			-g -O2
	ldflags:		

	xsltproc:		

```

for sudo make install:
```

Making install in src
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include"
 /usr/bin/install -c -m 644 'libdlo.h' '/usr/local/include/libdlo.h'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libdlo.la' '/usr/local/lib/libdlo.la'
libtool: install: /usr/bin/install -c .libs/libdlo.so.0.1.0 /usr/local/lib/libdlo.so.0.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libdlo.so.0.1.0 libdlo.so.0 || { rm -f libdlo.so.0 && ln -s libdlo.so.0.1.0 libdlo.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libdlo.so.0.1.0 libdlo.so || { rm -f libdlo.so && ln -s libdlo.so.0.1.0 libdlo.so; }; })
libtool: install: /usr/bin/install -c .libs/libdlo.lai /usr/local/lib/libdlo.la
libtool: install: /usr/bin/install -c .libs/libdlo.a /usr/local/lib/libdlo.a
libtool: install: chmod 644 /usr/local/lib/libdlo.a
libtool: install: ranlib /usr/local/lib/libdlo.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
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
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
Making install in test
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'test1' '/usr/local/bin/test1'
libtool: install: /usr/bin/install -c .libs/test1 /usr/local/bin/test1
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/libdlo" || /bin/mkdir -p "/usr/local/share/doc/libdlo"
 /usr/bin/install -c -m 644 'README' '/usr/local/share/doc/libdlo/README'
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
```
So here I see some Leaving Directory messages... Is that wrong/bad?

And finally the output for make check is:
```

Making check in src
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
Making check in test
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make  check-TESTS
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
test: argv[0]: /home/natalia/Downloads/libdlo-0.1.2/test/.libs/lt-test1
test: init...
test: no DisplayLink devices found
test: error 0 'Successful'
FAIL: test/test1
=======================================
1 of 1 test failed
Please report to libdlo@displaylink.com
=======================================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make: *** [check-recursive] Error 1
natalia@Inspiron11z:~/Downloads/libdlo-0.1.2$ 

```

The errors here are obvious... Any ideas what's the cause of them, or any way to fix them? Help and/or advices are highly appreciated. :)

---

