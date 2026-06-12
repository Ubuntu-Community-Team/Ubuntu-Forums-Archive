---
title: "Compiling under Ubuntu 8.04 Desktop"
date: 2008-07-17
forum: General Help
---

### Post by painejake on 2008-07-17
Im trying to compile MaNGOS a program that acts as a World of Warcraft server under Ubuntu for me and my girlfriend to play on. I'm fairly new to Linux but i has some ubuntu terminal experience. 

I get these errors when i try to build the solution and i am guessing these are why it is not working

Heres are the errors i get in the terminal:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
checking the maximum length of command line arguments... 98304
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
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for pthread_create in -lpthread... yes
checking for compress in -lz... yes
checking for ftime in -lcompat... no
checking for SHA1_Init in -lcrypto... yes
checking whether to build/link POSTGRESQL... no
checking whether to build/link MYSQL... yes
checking for mysql_config... no
checking whether to include debug info in library... no
checking whether cli console is enabled... yes
checking whether remote console is enabled... yes
checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking openssl/md5.h usability... yes
checking openssl/md5.h presence... yes
checking for openssl/md5.h... yes
checking openssl/rand.h usability... yes
checking openssl/rand.h presence... yes
checking for openssl/rand.h... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking openssl/sha.h usability... yes
checking openssl/sha.h presence... yes
checking for openssl/sha.h... yes
checking openssl/bn.h usability... yes
checking openssl/bn.h presence... yes
checking for openssl/bn.h... yes
checking mysql.h usability... no
checking mysql.h presence... no
checking for mysql.h... no
checking mysql/mysql.h usability... no
checking mysql/mysql.h presence... no
checking for mysql/mysql.h... no
checking libpq-fe.h usability... no
checking libpq-fe.h presence... no
checking for libpq-fe.h... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uint64_t... yes
checking for working volatile... yes
checking for ptrdiff_t... yes
checking whether closedir returns void... no
checking for error_at_line... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for atexit... yes
checking for ftime... yes
checking for gethostbyaddr... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for pow... no
checking for realpath... yes
checking for select... yes
checking for socket... yes
checking for sqrt... no
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes

```

Im guessing i am missing certain programs etc to help it compile successfully.  Can anyone please tell me what i need or need to do?

(Sorry if this is posted in the wrong section)

Many thanks!!

Jay :)

---

### Post by DirtDawg on 2008-07-17
Did you already install the build-essential package?

```
sudo apt-get install build-essential
```

---

### Post by painejake on 2008-07-17
No i didn't i will try that now. And god thanks for the fast reply!

EDIT: Ok i tried that i think it is producing less errors now. This is what i see in terminal now:

```
jake@Toshiba-satellite:~/sources/mangos$ ./configure --prefix=/home/jake/sources/mangos --sysconfdir=/home/jake/sources/mangos/etc --enable-cli --enable-ra --datadir=/home/jake/sources/mangos
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking the maximum length of command line arguments... 98304
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for pthread_create in -lpthread... yes
checking for compress in -lz... yes
checking for ftime in -lcompat... no
checking for SHA1_Init in -lcrypto... yes
checking whether to build/link POSTGRESQL... no
checking whether to build/link MYSQL... yes
checking for mysql_config... no
checking whether to include debug info in library... no
checking whether cli console is enabled... yes
checking whether remote console is enabled... yes
checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking openssl/md5.h usability... yes
checking openssl/md5.h presence... yes
checking for openssl/md5.h... yes
checking openssl/rand.h usability... yes
checking openssl/rand.h presence... yes
checking for openssl/rand.h... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking openssl/sha.h usability... yes
checking openssl/sha.h presence... yes
checking for openssl/sha.h... yes
checking openssl/bn.h usability... yes
checking openssl/bn.h presence... yes
checking for openssl/bn.h... yes
checking mysql.h usability... no
checking mysql.h presence... no
checking for mysql.h... no
checking mysql/mysql.h usability... no
checking mysql/mysql.h presence... no
checking for mysql/mysql.h... no
checking libpq-fe.h usability... no
checking libpq-fe.h presence... no
checking for libpq-fe.h... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uint64_t... yes
checking for working volatile... yes
checking for ptrdiff_t... yes
checking whether closedir returns void... no
checking for error_at_line... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for atexit... yes
checking for ftime... yes
checking for gethostbyaddr... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for pow... no
checking for realpath... yes
checking for select... yes
checking for socket... yes
checking for sqrt... no
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
configure: creating ./config.status
config.status: creating dep/include/Makefile
config.status: creating dep/lib/Makefile
config.status: creating dep/src/Makefile
config.status: creating dep/src/g3dlite/Makefile
config.status: creating dep/src/sockets/Makefile
config.status: creating dep/src/zlib/Makefile
config.status: creating dep/src/zthread/Makefile
config.status: creating dep/Makefile
config.status: creating doc/Doxyfile
config.status: creating doc/Makefile
config.status: creating Makefile
config.status: creating sql/Makefile
config.status: creating sql/tools/Makefile
config.status: creating sql/updates/Makefile
config.status: creating src/Makefile
config.status: creating src/framework/Makefile
config.status: creating src/shared/Makefile
config.status: creating src/shared/Auth/Makefile
config.status: creating src/shared/Config/Makefile
config.status: creating src/shared/Database/Makefile
config.status: creating src/shared/vmap/Makefile
config.status: creating src/shared/SystemConfig.h
config.status: creating src/game/Makefile
config.status: creating src/realmd/Makefile
config.status: creating src/realmd/realmd.conf
config.status: creating src/mangosd/Makefile
config.status: creating src/mangosd/mangosd.conf
config.status: creating src/bindings/Makefile
config.status: creating src/bindings/universal/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing svn_revision commands

```

---

### Post by painejake on 2008-07-17
Anyone have any ideas?

---

### Post by jerome1232 on 2008-07-17
looks like you are still missing packages, does it have a file called INSTALL or README that tells you what packages are needed, usually you have to hit synaptic and search for those packages, if there is no readme then I usually search synaptic for the pacakges it says it can't find during the configure and install the development versions ( -dev)

---

### Post by DirtDawg on 2008-07-17
Is that the full list of errors? It doesn't look to me like there are any errors at all. The last few lines of "errors" I see in your post are:
```
config.status: creating src/realmd/realmd.conf
config.status: creating src/mangosd/Makefile
config.status: creating src/mangosd/mangosd.conf
config.status: creating src/bindings/Makefile
config.status: creating src/bindings/universal/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing svn_revision commands
```
It doesn't look like there are any errors there. Usually, if there is a problem, the errors will tell you exactly what packages you are missing. If there are no errors, you should be able to run "make" and "sudo make install" with no problems. Maybe you could paste just the last, say, 30 lines or so of error messages?

Also, jerome1232 is correct. Usually there is a readme or install file that tells you what you need (or the website itself) and you will also need the "<package>-dev" variations of the required packages.

---

### Post by painejake on 2008-07-17
Well im trying now and it seems to be compiling fine :D 

Thanks ever so much for your help guys :) Ill post back if i have any more issuse

EDIT: Yep it worked :D Thanks again

---

