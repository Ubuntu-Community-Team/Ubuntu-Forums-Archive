---
title: "CANT INSTALL PowERTWEAK!!!!!"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by dreadkit.kat on 2009-09-07
when i go to install the Powertweak which i got from the link

[HTML]http://downloads.sourceforge.net/project/powertweak/powertweak/0.99.5/powertweak-0.99.5.tar.gz?use_mirror=nchc[/HTML]

I get this error

```
/home/indranil/Desktop/powertweak-0.99.5/INSTALL: 2: Compiling: not found
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
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
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether time.h and sys/time.h may both be included... yes
checking gpm.h usability... no
checking gpm.h presence... no
checking for gpm.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking for long... yes
checking size of long... 4
checking for void*... yes
checking size of void*... 4
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether struct tm is in sys/time.h or time.h... time.h
checking return type of signal handlers... void
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes
checking for error_at_line... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for atexit... yes
checking for bzero... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for munmap... yes
checking for pread... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strndup... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strstr... yes
checking for strerror... yes
checking for strtol... yes
checking for strtoul... yes
checking for uname... yes
Compiling CPU backend : yes
Compiling PCI backend : yes
Compiling /proc backend: yes
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: WARNING: Cannot find GTK: not building any UI!
checking for xml2-config... no
checking for xml2 - version >= 2.4.19... no
*** The xml2-config script installed by xml2 could not be found
*** If xml2 was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
checking for xml2-config... (cached) no
checking for xml2 - version >= 2.3.0... no
*** The xml2-config script installed by xml2 could not be found
*** If xml2 was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
checking for xml-config... no
checking for xml - version >= 2.1.0... no
*** The xml-config script installed by xml could not be found
*** If xml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML_CONFIG environment variable to the
*** full path to xml-config.
checking for xml-config... (cached) no
checking for xml - version >= 1.8.8... no
*** The xml-config script installed by xml could not be found
*** If xml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML_CONFIG environment variable to the
*** full path to xml-config.
configure: error: You need libxml version 1.8.8 or 2.1.0 and above
make: *** No targets specified and no makefile found.  Stop.
Password: 
```

And when i enter this password which is the super user password i guessed the terminal just closes.please help me solve this problem

---

### Post by oldos2er on 2009-09-07
That's really old software. What exactly does it tweak?

---

### Post by kwd on 2009-10-12
[QUOTE=dreadkit.kat;7912009]when i go to install the Powertweak which i got from the link

[HTML]http://downloads.sourceforge.net/project/powertweak/powertweak/0.99.5/powertweak-0.99.5.tar.gz?use_mirror=nchc[/HTML]

I get this error

[CODE]/home/indranil/Desktop/powertweak-0.99.5/INSTALL: 


I have not tried compiling PowerTweak... Yet. So I am no expert, but from reading the "Install" output you posted it looks like you need to install "libxml version 1.8.8 or 2.1.0 and above" and then try compiling the code again.

When a compile has an error, it tells you (though not very "loudly") and then exits.  Nothing more.

Good luck

---

