---
title: "Help with Inkscape please?"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by Ronchap on 2009-08-10
So I went to the inkscape website and wanted to install it myself. I downloaded the .tar.gz file. I have a site posted on helping me with installing .tar.gz files but, I am still having trouble. 

First, here is the link to the website. [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

Second, I got as far as making a directory for it, getting to the directory and extracting/unzipping it there.  I get as far as ./configure and I get this..

rchap@rchap-desktop:~/inkscape/inkscape-0.46$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
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
checking for intltool >= 0.22... 0.37.1 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool

The error at the end. Please explain.. in detail if you dont mind? I'm new to linux, just installed it yesterday. I really like to use the terminal for some reason, so if anything I can do from there would be nice :). Thanks!

---

### Post by AliTabuger7 on 2009-08-10
You must be missing a dependency:
[http://ubuntuforums.org/showthread.php?t=1080152](http://ubuntuforums.org/showthread.php?t=1080152)

```
sudo apt-get install gettext
```

---

### Post by Ronchap on 2009-08-10
Thanks, but theres another error. Something about a sanity check?

rchap@rchap-desktop:~/inkscape/inkscape-0.46$ sudo apt-get install gettext
[sudo] password for rchap: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cvs gettext-doc
The following NEW packages will be installed:
  gettext
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1910kB of archives.
After this operation, 7676kB of additional disk space will be used.
Get:1 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main gettext 0.17-6ubuntu2 [1910kB]
Fetched 1910kB in 2s (698kB/s)    
Selecting previously deselected package gettext.
(Reading database ... 125558 files and directories currently installed.)
Unpacking gettext (from .../gettext_0.17-6ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up gettext (0.17-6ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rchap@rchap-desktop:~/inkscape/inkscape-0.46$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
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
checking for intltool >= 0.22... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking for library containing strerror... no
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking dependency style of gcc... gcc3
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
rchap@rchap-desktop:~/inkscape/inkscape-0.46$ 

I opened the config.log file, but that is as confusing as this is to me at the moment.

---

### Post by AliTabuger7 on 2009-08-10
I noticed that it said you do not have g++ installed. That's probably important for this install.

```
sudo apt-get install build-essential
```

---

### Post by Ronchap on 2009-08-10
I should have asked this before I did the apt-get gettext. I am still in my inkscape directory when I did it. Does that matter? Hope not

---

### Post by AliTabuger7 on 2009-08-10
apt get is essentially a command line interface that does the same thing that "add/remove" does. It might make sense for you to use that instead, unless you want the very latest.

You could install inkscape using
```
sudo apt-get install inkscape
```

If that version is out of date, you may wish to find a .deb of the newer one.

If you would still like to install by compiling, I think i'll have to see that configure.log

---

### Post by Ronchap on 2009-08-10
Here is the full config.log. I'm just gonna assume you ment the whole log, so I went ahead and copied and pasted.

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by inkscape configure 0.46, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = rchap-desktop
uname -m = i686
uname -r = 2.6.28-14-generic
uname -s = Linux
uname -v = #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1988: checking build system type
configure:2006: result: i686-pc-linux-gnu
configure:2028: checking host system type
configure:2043: result: i686-pc-linux-gnu
configure:2081: checking for a BSD-compatible install
configure:2137: result: /usr/bin/install -c
configure:2148: checking whether build environment is sane
configure:2191: result: yes
configure:2219: checking for a thread-safe mkdir -p
configure:2258: result: /bin/mkdir -p
configure:2271: checking for gawk
configure:2301: result: no
configure:2271: checking for mawk
configure:2287: found /usr/bin/mawk
configure:2298: result: mawk
configure:2309: checking whether make sets $(MAKE)
configure:2330: result: yes
configure:2513: checking how to create a pax tar archive
configure:2526: tar --version
tar (GNU tar) 1.20
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by John Gilmore and Jay Fenlason.
configure:2529: $? = 0
configure:2569: tardir=conftest.dir && eval tar --format=posix -chf - "$tardir" >conftest.tar
configure:2572: $? = 0
configure:2576: tar -xf - <conftest.tar
configure:2579: $? = 0
configure:2592: result: gnutar
configure:2627: checking for style of include used by make
configure:2655: result: GNU
configure:2725: checking for gcc
configure:2741: found /usr/bin/gcc
configure:2752: result: gcc
configure:2990: checking for C compiler version
configure:2997: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3000: $? = 0
configure:3007: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:3010: $? = 0
configure:3017: gcc -V >&5
gcc: '-V' option must have argument
configure:3020: $? = 1
configure:3043: checking for C compiler default output file name
configure:3070: gcc    conftest.c  >&5
configure:3073: $? = 0
configure:3111: result: a.out
configure:3128: checking whether the C compiler works
configure:3138: ./a.out
configure:3141: $? = 0
configure:3158: result: yes
configure:3165: checking whether we are cross compiling
configure:3167: result: no
configure:3170: checking for suffix of executables
configure:3177: gcc -o conftest    conftest.c  >&5
configure:3180: $? = 0
configure:3204: result: 
configure:3210: checking for suffix of object files
configure:3236: gcc -c   conftest.c >&5
configure:3239: $? = 0
configure:3262: result: o
configure:3266: checking whether we are using the GNU C compiler
configure:3295: gcc -c   conftest.c >&5
configure:3301: $? = 0
configure:3318: result: yes
configure:3323: checking whether gcc accepts -g
configure:3353: gcc -c -g  conftest.c >&5
configure:3359: $? = 0
configure:3458: result: yes
configure:3475: checking for gcc option to accept ISO C89
configure:3549: gcc  -c -g -O2  conftest.c >&5
configure:3555: $? = 0
configure:3578: result: none needed
configure:3598: checking dependency style of gcc
configure:3689: result: gcc3
configure:3717: checking for intltool >= 0.22
configure:3724: result: 0.37.1 found
configure:3775: checking for xgettext
configure:3793: found /usr/bin/xgettext
configure:3805: result: /usr/bin/xgettext
configure:3815: checking for msgmerge
configure:3833: found /usr/bin/msgmerge
configure:3845: result: /usr/bin/msgmerge
configure:3855: checking for msgfmt
configure:3873: found /usr/bin/msgfmt
configure:3885: result: /usr/bin/msgfmt
configure:3917: checking for perl
configure:3935: found /usr/bin/perl
configure:3947: result: /usr/bin/perl
configure:3966: checking for XML::Parser
configure:3969: result: ok
configure:4006: gcc -o conftest -g -O2   conftest.c  >&5
configure:4012: $? = 0
configure:4196: checking for g++
configure:4212: found /usr/bin/g++
configure:4223: result: g++
configure:4254: checking for C++ compiler version
configure:4261: g++ --version >&5
g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4264: $? = 0
configure:4271: g++ -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:4274: $? = 0
configure:4281: g++ -V >&5
g++: '-V' option must have argument
configure:4284: $? = 1
configure:4287: checking whether we are using the GNU C++ compiler
configure:4316: g++ -c   conftest.cpp >&5
configure:4322: $? = 0
configure:4339: result: yes
configure:4344: checking whether g++ accepts -g
configure:4374: g++ -c -g  conftest.cpp >&5
configure:4380: $? = 0
configure:4479: result: yes
configure:4504: checking dependency style of g++
configure:4595: result: gcc3
configure:4611: checking for library containing strerror
configure:4652: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:4658: $? = 0
configure:4686: result: none required
configure:4810: checking for C++ compiler version
configure:4817: g++ --version >&5
g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4820: $? = 0
configure:4827: g++ -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:4830: $? = 0
configure:4837: g++ -V >&5
g++: '-V' option must have argument
configure:4840: $? = 1
configure:4843: checking whether we are using the GNU C++ compiler
configure:4895: result: yes
configure:4900: checking whether g++ accepts -g
configure:5035: result: yes
configure:5060: checking dependency style of g++
configure:5151: result: gcc3
configure:5214: checking for gcc
configure:5241: result: gcc
configure:5479: checking for C compiler version
configure:5486: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:5489: $? = 0
configure:5496: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:5499: $? = 0
configure:5506: gcc -V >&5
gcc: '-V' option must have argument
configure:5509: $? = 1
configure:5512: checking whether we are using the GNU C compiler
configure:5564: result: yes
configure:5569: checking whether gcc accepts -g
configure:5704: result: yes
configure:5721: checking for gcc option to accept ISO C89
configure:5824: result: none needed
configure:5844: checking dependency style of gcc
configure:5935: result: gcc3
configure:5962: checking dependency style of gcc
configure:6053: result: gcc3
configure:6073: checking how to run the C++ preprocessor
configure:6109: g++ -E  conftest.cpp
configure:6115: $? = 0
configure:6146: g++ -E  conftest.cpp
conftest.cpp:10:28: error: ac_nonexistent.h: No such file or directory
configure:6152: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "inkscape"
| #define PACKAGE_TARNAME "inkscape"
| #define PACKAGE_VERSION "0.46"
| #define PACKAGE_STRING "inkscape 0.46"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "inkscape"
| #define VERSION "0.46"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6185: result: g++ -E
configure:6214: g++ -E  conftest.cpp
configure:6220: $? = 0
configure:6251: g++ -E  conftest.cpp
conftest.cpp:10:28: error: ac_nonexistent.h: No such file or directory
configure:6257: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "inkscape"
| #define PACKAGE_TARNAME "inkscape"
| #define PACKAGE_VERSION "0.46"
| #define PACKAGE_STRING "inkscape 0.46"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "inkscape"
| #define VERSION "0.46"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6295: checking for grep that handles long lines and -e
configure:6369: result: /bin/grep
configure:6374: checking for egrep
configure:6452: result: /bin/grep -E
configure:6457: checking for ANSI C header files
configure:6487: g++ -c -g -O2  conftest.cpp >&5
configure:6493: $? = 0
configure:6592: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:6595: $? = 0
configure:6601: ./conftest
configure:6604: $? = 0
configure:6621: result: yes
configure:6680: checking for gcc
configure:6707: result: gcc
configure:6945: checking for C compiler version
configure:6952: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:6955: $? = 0
configure:6962: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:6965: $? = 0
configure:6972: gcc -V >&5
gcc: '-V' option must have argument
configure:6975: $? = 1
configure:6978: checking whether we are using the GNU C compiler
configure:7030: result: yes
configure:7035: checking whether gcc accepts -g
configure:7170: result: yes
configure:7187: checking for gcc option to accept ISO C89
configure:7290: result: none needed
configure:7310: checking dependency style of gcc
configure:7401: result: gcc3
configure:7417: checking whether gcc and cc understand -c and -o together
configure:7452: gcc -c conftest.cpp -o conftest2.o >&5
configure:7455: $? = 0
configure:7461: gcc -c conftest.cpp -o conftest2.o >&5
configure:7464: $? = 0
configure:7475: cc -c conftest.cpp >&5
configure:7478: $? = 0
configure:7486: cc -c conftest.cpp -o conftest2.o >&5
configure:7489: $? = 0
configure:7495: cc -c conftest.cpp -o conftest2.o >&5
configure:7498: $? = 0
configure:7516: result: yes
configure:7542: Testing -Wno-pointer-sign
configure:7578: gcc -c -Wno-pointer-sign -g -O2  conftest.c >&5
configure:7584: $? = 0
configure:7589:  compiler supports -Wno-pointer-sign
configure:7653: checking for ranlib
configure:7669: found /usr/bin/ranlib
configure:7680: result: ranlib
configure:7708: checking GNU compiler version
configure:7716: result: 4.3.3
configure:7757: checking for sys/types.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for sys/stat.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for stdlib.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for string.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for memory.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for strings.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for inttypes.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for stdint.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7757: checking for unistd.h
configure:7778: g++ -c -g -O2  conftest.cpp >&5
configure:7784: $? = 0
configure:7800: result: yes
configure:7828: checking locale.h usability
configure:7845: g++ -c -g -O2  conftest.cpp >&5
configure:7851: $? = 0
configure:7865: result: yes
configure:7869: checking locale.h presence
configure:7884: g++ -E  conftest.cpp
configure:7890: $? = 0
configure:7904: result: yes
configure:7932: checking for locale.h
configure:7940: result: yes
configure:7954: checking for LC_MESSAGES
configure:7980: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:7986: $? = 0
configure:8003: result: yes
configure:8032: checking libintl.h usability
configure:8049: g++ -c -g -O2  conftest.cpp >&5
configure:8055: $? = 0
configure:8069: result: yes
configure:8073: checking libintl.h presence
configure:8088: g++ -E  conftest.cpp
configure:8094: $? = 0
configure:8108: result: yes
configure:8136: checking for libintl.h
configure:8143: result: yes
configure:8154: checking for ngettext in libc
configure:8182: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:8188: $? = 0
configure:8206: result: yes
configure:8210: checking for dgettext in libc
configure:8238: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:8244: $? = 0
configure:8262: result: yes
configure:8271: checking for bind_textdomain_codeset
configure:8327: g++ -o conftest -g -O2   conftest.cpp  >&5
configure:8333: $? = 0
configure:8351: result: yes
configure:8838: checking for msgfmt
configure:8865: result: /usr/bin/msgfmt
configure:8878: checking for dcgettext
configure:8934: g++ -o conftest -g -O2   conftest.cpp   >&5
configure:8940: $? = 0
configure:8958: result: yes
configure:8969: checking if msgfmt accepts -c
configure:8984: $MSGFMT -c -o /dev/null conftest.foo
configure:8987: $? = 0
configure:8989: result: yes
configure:8999: checking for gmsgfmt
configure:9030: result: /usr/bin/msgfmt
configure:9040: checking for xgettext
configure:9067: result: /usr/bin/xgettext
configure:9096: g++ -o conftest -g -O2   conftest.cpp   >&5
configure:9102: $? = 0
configure:9271: checking for catalogs to be installed
configure:9296: result:  am ar az be bg bn br ca ca@valencia cs da de dz el en_AU en_CA en_GB en_US@piglatin eo es_MX es et eu fi fr ga gl he hr hu id it ja km ko lt mk mn nb ne nl nn pa pl pt_BR pt ro ru rw sk sl sq sr@latin sr sv th tr uk vi zh_CN zh_TW
configure:9331: checking for pkg-config
configure:9349: found /usr/bin/pkg-config
configure:9362: result: /usr/bin/pkg-config
configure:9378: checking for msgfmt
configure:9409: result: /usr/bin/msgfmt
configure:9419: checking for gmsgfmt
configure:9450: result: /usr/bin/msgfmt
configure:9459: checking for png_read_info in -lpng
configure:9494: g++ -o conftest -g -O2   conftest.cpp -lpng -lz -lm  >&5
/usr/bin/ld: cannot find -lpng
collect2: ld returned 1 exit status
configure:9500: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "inkscape"
| #define PACKAGE_TARNAME "inkscape"
| #define PACKAGE_VERSION "0.46"
| #define PACKAGE_STRING "inkscape 0.46"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "inkscape"
| #define VERSION "0.46"
| #define STDC_HEADERS 1
| #define GETTEXT_PACKAGE "inkscape"
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_LC_MESSAGES 1
| #define HAVE_BIND_TEXTDOMAIN_CODESET 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define ENABLE_NLS 1
| /* end confdefs.h.  */
| 
| /* Override any GCC internal prototype to avoid an error.
|    Use char because int might match the return type of a GCC
|    builtin and then its argument prototype would still apply.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| char png_read_info ();
| int
| main ()
| {
| return png_read_info ();
|   ;
|   return 0;
| }
configure:9518: result: no
configure:9658: error: libpng >= 1.2 is needed to compile inkscape

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CAIRO_PDF_CFLAGS_set=
ac_cv_env_CAIRO_PDF_CFLAGS_value=
ac_cv_env_CAIRO_PDF_LIBS_set=
ac_cv_env_CAIRO_PDF_LIBS_value=
ac_cv_env_CAIRO_SVG_CFLAGS_set=
ac_cv_env_CAIRO_SVG_CFLAGS_value=
ac_cv_env_CAIRO_SVG_LIBS_set=
ac_cv_env_CAIRO_SVG_LIBS_value=
ac_cv_env_CCASFLAGS_set=
ac_cv_env_CCASFLAGS_value=
ac_cv_env_CCAS_set=
ac_cv_env_CCAS_value=
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_GNOME_VFS_CFLAGS_set=
ac_cv_env_GNOME_VFS_CFLAGS_value=
ac_cv_env_GNOME_VFS_LIBS_set=
ac_cv_env_GNOME_VFS_LIBS_value=
ac_cv_env_INKBOARD_CFLAGS_set=
ac_cv_env_INKBOARD_CFLAGS_value=
ac_cv_env_INKBOARD_LIBS_set=
ac_cv_env_INKBOARD_LIBS_value=
ac_cv_env_INKSCAPE_CFLAGS_set=
ac_cv_env_INKSCAPE_CFLAGS_value=
ac_cv_env_INKSCAPE_LIBS_set=
ac_cv_env_INKSCAPE_LIBS_value=
ac_cv_env_LCMS_CFLAGS_set=
ac_cv_env_LCMS_CFLAGS_value=
ac_cv_env_LCMS_LIBS_set=
ac_cv_env_LCMS_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_LIBWPG_CFLAGS_set=
ac_cv_env_LIBWPG_CFLAGS_value=
ac_cv_env_LIBWPG_LIBS_set=
ac_cv_env_LIBWPG_LIBS_value=
ac_cv_env_PANGOFT2_CFLAGS_set=
ac_cv_env_PANGOFT2_CFLAGS_value=
ac_cv_env_PANGOFT2_LIBS_set=
ac_cv_env_PANGOFT2_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_POPPLER_CAIRO_CFLAGS_set=
ac_cv_env_POPPLER_CAIRO_CFLAGS_value=
ac_cv_env_POPPLER_CAIRO_LIBS_set=
ac_cv_env_POPPLER_CAIRO_LIBS_value=
ac_cv_env_POPPLER_CFLAGS_set=
ac_cv_env_POPPLER_CFLAGS_value=
ac_cv_env_POPPLER_GLIB_CFLAGS_set=
ac_cv_env_POPPLER_GLIB_CFLAGS_value=
ac_cv_env_POPPLER_GLIB_LIBS_set=
ac_cv_env_POPPLER_GLIB_LIBS_value=
ac_cv_env_POPPLER_LIBS_set=
ac_cv_env_POPPLER_LIBS_value=
ac_cv_env_XFT_CFLAGS_set=
ac_cv_env_XFT_CFLAGS_value=
ac_cv_env_XFT_LIBS_set=
ac_cv_env_XFT_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_func_bind_textdomain_codeset=yes
ac_cv_func_dcgettext=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_libintl_h=yes
ac_cv_header_locale_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_lib_png_png_read_info=no
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GMSGFMT=/usr/bin/msgfmt
ac_cv_path_GREP=/bin/grep
ac_cv_path_INTLTOOL_PERL=/usr/bin/perl
ac_cv_path_MSGFMT=/usr/bin/msgfmt
ac_cv_path_MSGMERGE=/usr/bin/msgmerge
ac_cv_path_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_XGETTEXT=/usr/bin/xgettext
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_CXXCPP='g++ -E'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cc_gcc_c_o=yes
ac_cv_prog_cxx_g=yes
ac_cv_prog_make_make_set=yes
ac_cv_search_strerror='none required'
am_cv_CCAS_dependencies_compiler_type=gcc3
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
am_cv_prog_cc_stdc=
am_cv_prog_tar_pax=gnutar
am_cv_val_LC_MESSAGES=yes
gt_cv_func_dgettext_libc=yes
gt_cv_func_dgettext_libintl=no
gt_cv_func_ngettext_libc=yes
gt_cv_have_gettext=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run aclocal-1.10 '
ALL_LINGUAS='am ar az be bg bn br ca ca@valencia cs da de dz el en_AU en_CA en_GB en_US@piglatin eo es_MX es et eu fi fr ga gl he hr hu id it ja km ko lt mk mn nb ne nl nn pa pl pt_BR pt ro ru rw sk sl sq sr@latin sr sv th tr uk vi zh_CN zh_TW'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run tar'
AUTOCONF='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run autoconf'
AUTOHEADER='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run autoheader'
AUTOMAKE='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run automake-1.10'
AWK='mawk'
CAIRO_PDF_CFLAGS=''
CAIRO_PDF_LIBS=''
CAIRO_SVG_CFLAGS=''
CAIRO_SVG_LIBS=''
CARBON_LDFLAGS=''
CATALOGS=' am.gmo ar.gmo az.gmo be.gmo bg.gmo bn.gmo br.gmo ca.gmo [email]ca@valencia.gmo[/email] cs.gmo da.gmo de.gmo dz.gmo el.gmo en_AU.gmo en_CA.gmo en_GB.gmo [email]en_US@piglatin.gmo[/email] eo.gmo es_MX.gmo es.gmo et.gmo eu.gmo fi.gmo fr.gmo ga.gmo gl.gmo he.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo km.gmo ko.gmo lt.gmo mk.gmo mn.gmo nb.gmo ne.gmo nl.gmo nn.gmo pa.gmo pl.gmo pt_BR.gmo pt.gmo ro.gmo ru.gmo rw.gmo sk.gmo sl.gmo sq.gmo [email]sr@latin.gmo[/email] sr.gmo sv.gmo th.gmo tr.gmo uk.gmo vi.gmo zh_CN.gmo zh_TW.gmo'
CATOBJEXT='.gmo'
CC='gcc'
CCAS='gcc'
CCASDEPMODE='depmode=gcc3'
CCASFLAGS='-g -O2'
CCDEPMODE='depmode=gcc3'
CFLAGS='-Wall -Wformat-security -W -D_FORTIFY_SOURCE=2 -Wno-pointer-sign -g -O2'
CPPFLAGS=''
CXX='g++'
CXXCPP='g++ -E'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CYGPATH_W='echo'
DATADIRNAME='share'
DEFS=''
DEPDIR='.deps'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
FREETYPE_CFLAGS=''
FREETYPE_CONFIG=''
FREETYPE_LIBS=''
GETTEXT_PACKAGE='inkscape'
GMOFILES=' am.gmo ar.gmo az.gmo be.gmo bg.gmo bn.gmo br.gmo ca.gmo [email]ca@valencia.gmo[/email] cs.gmo da.gmo de.gmo dz.gmo el.gmo en_AU.gmo en_CA.gmo en_GB.gmo [email]en_US@piglatin.gmo[/email] eo.gmo es_MX.gmo es.gmo et.gmo eu.gmo fi.gmo fr.gmo ga.gmo gl.gmo he.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo km.gmo ko.gmo lt.gmo mk.gmo mn.gmo nb.gmo ne.gmo nl.gmo nn.gmo pa.gmo pl.gmo pt_BR.gmo pt.gmo ro.gmo ru.gmo rw.gmo sk.gmo sl.gmo sq.gmo [email]sr@latin.gmo[/email] sr.gmo sv.gmo th.gmo tr.gmo uk.gmo vi.gmo zh_CN.gmo zh_TW.gmo'
GMSGFMT='/usr/bin/msgfmt'
GNOME_VFS_CFLAGS=''
GNOME_VFS_LIBS=''
GREP='/bin/grep'
HAVE_CARBON_FALSE=''
HAVE_CARBON_TRUE=''
IMAGEMAGICK_LIBS=''
INKBOARD_CFLAGS=''
INKBOARD_LIBS=''
INKJAR_FALSE=''
INKJAR_TRUE=''
INKSCAPE_CFLAGS=''
INKSCAPE_DATADIR=''
INKSCAPE_LIBDIR=''
INKSCAPE_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
INSTOBJEXT='.mo'
INTLLIBS=''
INTLTOOL_CAVES_RULE='%.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DESKTOP_RULE='%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DIRECTORY_RULE='%.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_EXTRACT='$(top_builddir)/intltool-extract'
INTLTOOL_KBD_RULE='%.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_KEYS_RULE='%.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_MERGE='$(top_builddir)/intltool-merge'
INTLTOOL_OAF_RULE='%.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@'
INTLTOOL_PERL='/usr/bin/perl'
INTLTOOL_POLICY_RULE='%.policy:    %.policy.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_PONG_RULE='%.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_PROP_RULE='%.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SCHEMAS_RULE='%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVER_RULE='%.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVICE_RULE='%.service: %.service.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SHEET_RULE='%.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SOUNDLIST_RULE='%.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_THEME_RULE='%.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UI_RULE='%.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UPDATE='$(top_builddir)/intltool-update'
INTLTOOL_XAM_RULE='%.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_XML_NOMERGE_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@'
INTLTOOL_XML_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
LCMS_CFLAGS=''
LCMS_LIBS=''
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBWPG_CFLAGS=''
LIBWPG_LIBS=''
LTLIBOBJS=''
MAGICKPP_CONFIG=''
MAKEINFO='${SHELL} /home/rchap/inkscape/inkscape-0.46/missing --run makeinfo'
MKINSTALLDIRS='./mkinstalldirs'
MSGFMT='/usr/bin/msgfmt'
MSGFMT_OPTS='-c'
MSGMERGE='/usr/bin/msgmerge'
OBJEXT='o'
PACKAGE='inkscape'
PACKAGE_BUGREPORT=''
PACKAGE_LOCALE_DIR=''
PACKAGE_NAME='inkscape'
PACKAGE_STRING='inkscape 0.46'
PACKAGE_TARNAME='inkscape'
PACKAGE_VERSION='0.46'
PANGOFT2_CFLAGS=''
PANGOFT2_LIBS=''
PATH_SEPARATOR=':'
PERL_CFLAGS=''
PERL_LIBS=''
PKG_CONFIG='/usr/bin/pkg-config'
PLATFORM_SOLARIS_2_8_FALSE=''
PLATFORM_SOLARIS_2_8_TRUE=''
PLATFORM_WIN32_FALSE=''
PLATFORM_WIN32_TRUE=''
POFILES=' am.po ar.po az.po be.po bg.po bn.po br.po ca.po [email]ca@valencia.po[/email] cs.po da.po de.po dz.po el.po en_AU.po en_CA.po en_GB.po [email]en_US@piglatin.po[/email] eo.po es_MX.po es.po et.po eu.po fi.po fr.po ga.po gl.po he.po hr.po hu.po id.po it.po ja.po km.po ko.po lt.po mk.po mn.po nb.po ne.po nl.po nn.po pa.po pl.po pt_BR.po pt.po ro.po ru.po rw.po sk.po sl.po sq.po [email]sr@latin.po[/email] sr.po sv.po th.po tr.po uk.po vi.po zh_CN.po zh_TW.po'
POPPLER_CAIRO_CFLAGS=''
POPPLER_CAIRO_LIBS=''
POPPLER_CFLAGS=''
POPPLER_GLIB_CFLAGS=''
POPPLER_GLIB_LIBS=''
POPPLER_LIBS=''
POSUB='po'
POW_LIB=''
PO_IN_DATADIR_FALSE=''
PO_IN_DATADIR_TRUE=''
PYTHON_CFLAGS=''
PYTHON_LIBS=''
RANLIB='ranlib'
RELAYTOOL_PROG=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
USE_GNOME_VFS_FALSE=''
USE_GNOME_VFS_TRUE=''
USE_IMAGE_MAGICK_FALSE=''
USE_IMAGE_MAGICK_TRUE=''
USE_LCMS_FALSE=''
USE_LCMS_TRUE=''
USE_MMX_FALSE=''
USE_MMX_TRUE=''
USE_NLS='yes'
USE_XFT_FALSE=''
USE_XFT_TRUE=''
VERSION='0.46'
WITH_INKBOARD_FALSE=''
WITH_INKBOARD_TRUE=''
WITH_LIBWPG_FALSE=''
WITH_LIBWPG_TRUE=''
WITH_PERL_FALSE=''
WITH_PERL_TRUE=''
WITH_PYTHON_FALSE=''
WITH_PYTHON_TRUE=''
XFT_CFLAGS=''
XFT_LIBS=''
XGETTEXT='/usr/bin/xgettext'
ac_ct_CC='gcc'
ac_ct_CXX='g++'
am__fastdepCCAS_FALSE='#'
am__fastdepCCAS_TRUE=''
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='tar --format=posix -chf - "$$tardir"'
am__untar='tar -xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/rchap/inkscape/inkscape-0.46/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "inkscape"
#define PACKAGE_TARNAME "inkscape"
#define PACKAGE_VERSION "0.46"
#define PACKAGE_STRING "inkscape 0.46"
#define PACKAGE_BUGREPORT ""
#define PACKAGE "inkscape"
#define VERSION "0.46"
#define STDC_HEADERS 1
#define GETTEXT_PACKAGE "inkscape"
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STRINGS_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_LOCALE_H 1
#define HAVE_LC_MESSAGES 1
#define HAVE_BIND_TEXTDOMAIN_CODESET 1
#define HAVE_GETTEXT 1
#define HAVE_DCGETTEXT 1
#define ENABLE_NLS 1

configure: exit 1


After i did the command, sudo apt-get install build-essential, I did ./configure again, but this time, at the end of the terminal config log, it said 
"configure: error: libpng >= 1.2 is needed to compile inkscape"

---

### Post by AliTabuger7 on 2009-08-11
```
sudo apt-get install libpng-dev
```

---

