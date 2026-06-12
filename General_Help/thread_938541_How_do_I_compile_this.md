---
title: "How do I compile this?"
date: 2008-10-05
forum: General Help
---

### Post by johnnyxxxcakes on 2008-10-05
I'm using Audacious as my current media player on Ubuntu, and I discovered that there's a 31-band EQ out there for this program. I'm not too good with compiling, and I was wondering what I might've been doing wrong here.

I'll post what I entered in the terminal here:
john@john-laptop:~$ cd eq-audacious-0.21
john@john-laptop:~/eq-audacious-0.21$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for correct ltmain.sh version... yes
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
checking for prefix by checking for audacious... /usr/bin/audacious
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for old style FreeBSD -pthread flag... no
checking for pthread_attr_init in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AUDACIOUS... configure: error: Can't find the Audacious SDK.
john@john-laptop:~/eq-audacious-0.21$ make
make: *** No targets specified and no makefile found.  Stop.

Does anyone have any idea what to do next? Any help is appreciated.

---

### Post by OutOfReach on 2008-10-05
There should usually be a README, or INSTALL text file that tells you the instructions of compiling. Is there not?

---

### Post by johnnyxxxcakes on 2008-10-05
> **OutOfReach said:**
> There should usually be a README, or INSTALL text file that tells you the instructions of compiling. Is there not?

I found a README file and it says the following in the installation category:

> Compiling/Installing
  ====================
  - For the anxious:
    Just type 
  
      #./configure && make && make install

    from the command line.

I typed exactly what they wanted me to, and all I get is this:

john@john-laptop:~$ cd eq-audacious-0.21
john@john-laptop:~/eq-audacious-0.21$ #./configure && make && make install
john@john-laptop:~/eq-audacious-0.21$ 

I'm in the current directory of the folder where all the files are located (/home/eq-audacious-0.21).

---

### Post by OutOfReach on 2008-10-05
I think that they mean:
```
sudo ./configure && make && make install
```

since make install usually requires root permissions.

---

### Post by rsambuca on 2008-10-05
I wouldn't recommend doing it that way.  Run each line separately.```
./configure
make
sudo make install
```

---

### Post by johnnyxxxcakes on 2008-10-05
> **OutOfReach said:**
> I think that they mean:
```
sudo ./configure && make && make install
```

since make install usually requires root permissions.

Okay, I tried that and the terminal keeps ending with the line:
> checking for AUDACIOUS... configure: error: Can't find the Audacious SDK.

---

### Post by johnnyxxxcakes on 2008-10-05
> **rsambuca said:**
> I wouldn't recommend doing it that way.  Run each line separately.```
./configure
make
sudo make install
```

When I tried 'make' I get this error:
> john@john-laptop:~/eq-audacious-0.21$ make
make: *** No targets specified and no makefile found.  Stop.


---

### Post by shirilover on 2008-10-05
You need to install the audacious-dev package, if you have not done so.

---

### Post by johnnyxxxcakes on 2008-10-05
> **shirilover said:**
> You need to install the audacious-dev package, if you have not done so.

Alright, I installed the audacious-dev package, and then I tried ./configure again and I get this in return:

> john@john-laptop:~/eq-audacious-0.21$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for correct ltmain.sh version... yes
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
checking for prefix by checking for audacious... /usr/bin/audacious
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for old style FreeBSD -pthread flag... no
checking for pthread_attr_init in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AUDACIOUS... yes
checking for ANSI C header files... (cached) yes
checking for sort... /usr/bin/sort
checking for uniq... /usr/bin/uniq
checking for Effect plugin dir... /usr/lib/audacious/Effect
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

  Configuration:
  Install path              : /usr/lib/audacious/Effect
  Debug compilation flags   : no
  Benchmark code            : no
  CPU features detection    : yes
  3DNow/MMX code            : no
  SSE code                  : no
  SSE2 code                 : yes
  SSE filter implementation : yes

john@john-laptop:~/eq-audacious-0.21$ 


And then 'make'
> john@john-laptop:~/eq-audacious-0.21$ make
make  all-recursive
make[1]: Entering directory `/home/john/eq-audacious-0.21'
Making all in src
make[2]: Entering directory `/home/john/eq-audacious-0.21/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/eq-audacious-0.21/src'
make[2]: Entering directory `/home/john/eq-audacious-0.21'
make[2]: Leaving directory `/home/john/eq-audacious-0.21'
make[1]: Leaving directory `/home/john/eq-audacious-0.21'
john@john-laptop:~/eq-audacious-0.21$ 


And I still get nothing.

---

### Post by timstone on 2008-10-05
got this right from the audacious website...

>   When compiling audacious modules, ./configure keeps telling me it can't find the Audacious SDK!

You probably installed to /usr/local. This means that the pkg-config metadata for Audacious was also installed to /usr/local. The following code will provide a hint to pkg-config as where it can find Audacious' SDK:

 $ export PKG_CONFIG_PATH="/usr/X11R6/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/lib/pkgconfig"

Then you should be able to compile like normal. Please note that if you are using C Shell, you will need to use the setenv command instead of export. 

---

### Post by johnnyxxxcakes on 2008-10-05
> **timstone said:**
> got this right from the audacious website...

Well after I installed the audacious-dev files, it seems to go a lot farther in the terminal than it did before, so I think this issue has been resolved.

But thanks anyway. :)

---

### Post by tonybaqain on 2008-10-05
dear johnnyxxxcakes,

this -> 
```

john@john-laptop:~/eq-audacious-0.21$ make
make all-recursive
make[1]: Entering directory `/home/john/eq-audacious-0.21'
Making all in src
make[2]: Entering directory `/home/john/eq-audacious-0.21/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/eq-audacious-0.21/src'
make[2]: Entering directory `/home/john/eq-audacious-0.21'
make[2]: Leaving directory `/home/john/eq-audacious-0.21'
make[1]: Leaving directory `/home/john/eq-audacious-0.21'
john@john-laptop:~/eq-audacious-0.21$ 

```

means that you have sucessfully compiled it, try ```
sudo make install
``` or to be more convinced with compiling do a ```
 make clean && make && sudo make install
```

there you go, and have fun :)

---

### Post by johnnyxxxcakes on 2008-10-05
> **tonybaqain said:**
> dear johnnyxxxcakes,

this -> 
```

john@john-laptop:~/eq-audacious-0.21$ make
make all-recursive
make[1]: Entering directory `/home/john/eq-audacious-0.21'
Making all in src
make[2]: Entering directory `/home/john/eq-audacious-0.21/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/eq-audacious-0.21/src'
make[2]: Entering directory `/home/john/eq-audacious-0.21'
make[2]: Leaving directory `/home/john/eq-audacious-0.21'
make[1]: Leaving directory `/home/john/eq-audacious-0.21'
john@john-laptop:~/eq-audacious-0.21$ 

```

means that you have sucessfully compiled it, try ```
sudo make install
``` or to be more convinced with compiling do a ```
 make clean && make && sudo make install
```

there you go, and have fun :)

With the 'sudo make install' command, I get the following:
> john@john-laptop:~/eq-audacious-0.21$ sudo make install
Making install in src
make[1]: Entering directory `/home/john/eq-audacious-0.21/src'
make[2]: Entering directory `/home/john/eq-audacious-0.21/src'
/bin/bash ../mkinstalldirs /usr/lib/audacious/Effect
 /bin/bash ../libtool --mode=install /usr/bin/install -c  libeq.la /usr/lib/audacious/Effect/libeq.la
/usr/bin/install -c .libs/libeq.so /usr/lib/audacious/Effect/libeq.so
/usr/bin/install -c .libs/libeq.lai /usr/lib/audacious/Effect/libeq.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/audacious/Effect
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/audacious/Effect

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
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/john/eq-audacious-0.21/src'
make[1]: Leaving directory `/home/john/eq-audacious-0.21/src'
make[1]: Entering directory `/home/john/eq-audacious-0.21'
make[2]: Entering directory `/home/john/eq-audacious-0.21'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/john/eq-audacious-0.21'
make[1]: Leaving directory `/home/john/eq-audacious-0.21'
john@john-laptop:~/eq-audacious-0.21$ 


Is that correct?

---

### Post by tonybaqain on 2008-10-05
it says for you 
```

Libraries have been installed in:
/usr/lib/audacious/Effect

```

then they are installed.
have fun :)

---

### Post by johnnyxxxcakes on 2008-10-05
> **tonybaqain said:**
> it says for you 
```

Libraries have been installed in:
/usr/lib/audacious/Effect

```

then they are installed.
have fun :)

Alright, but I'm not finding this 31-band EQ in Audacious. :-k

---

### Post by johnnyxxxcakes on 2008-10-06
If it's installed, then where would the plugin file be located?

---

### Post by Meow27 on 2008-10-06
just popping in: when you complete doing 'make' there should be some sort of executable within the folder you compiled the program (make install the program inside the folder and make install installs it to the system... some programs require you to do make install in order for it to function)

---

