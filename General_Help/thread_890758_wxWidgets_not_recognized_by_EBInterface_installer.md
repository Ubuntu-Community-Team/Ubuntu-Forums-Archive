---
title: "wxWidgets not recognized by EBInterface installer"
date: 2008-08-15
forum: General Help
---

### Post by Sam324 on 2008-08-15
Hi, I installed wxWidgets just like it said on the website (and added the key too), but it gives me a "No wx-config" error.  Here's the I/O:
```

[COLOR=Blue]sam@Sam-ubuntu:~/EBInterface$[/COLOR] [COLOR=Green]sudo apt-get install python-wxgtk2.8 python-wxtools python-wxaddons wx2.8-i18n[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2ldbl libgtk1.2-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwxbase2.8-0 libwxgtk2.8-0 python-wxversion
Suggested packages:
  python-xml wx2.8-doc wx2.8-examples
The following NEW packages will be installed:
  libwxbase2.8-0 libwxgtk2.8-0 python-wxaddons python-wxgtk2.8 python-wxtools
  python-wxversion wx2.8-i18n
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.6MB of archives.
After this operation, 52.2MB of additional disk space will be used.
Do you want to continue [Y/n]? [COLOR=Green]y[/COLOR]
Selecting previously deselected package libwxbase2.8-0.
(Reading database ... 120460 files and directories currently installed.)
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.8.1-0_amd64.deb) ...
Selecting previously deselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.8.1-0_amd64.deb) ...
Selecting previously deselected package python-wxversion.
Unpacking python-wxversion (from .../python-wxversion_2.8.8.1-0_all.deb) ...
Selecting previously deselected package python-wxgtk2.8.
Unpacking python-wxgtk2.8 (from .../python-wxgtk2.8_2.8.8.1-0_amd64.deb) ...
Selecting previously deselected package python-wxaddons.
Unpacking python-wxaddons (from .../python-wxaddons_2.8.8.1-0_all.deb) ...
Selecting previously deselected package python-wxtools.
Unpacking python-wxtools (from .../python-wxtools_2.8.8.1-0_all.deb) ...
Selecting previously deselected package wx2.8-i18n.
Unpacking wx2.8-i18n (from .../wx2.8-i18n_2.8.8.1-0_all.deb) ...
Setting up libwxbase2.8-0 (2.8.8.1-0) ...

Setting up libwxgtk2.8-0 (2.8.8.1-0) ...

Setting up python-wxversion (2.8.8.1-0) ...

Setting up python-wxgtk2.8 (2.8.8.1-0) ...

Setting up python-wxaddons (2.8.8.1-0) ...

Setting up python-wxtools (2.8.8.1-0) ...

Setting up wx2.8-i18n (2.8.8.1-0) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[COLOR=Blue]sam@Sam-ubuntu:~/EBInterface$[/COLOR] [COLOR=Green]./configure[/COLOR]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
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
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
[COLOR=Red]checking wxWidgets version... ./configure: line 19414: wx-config: command not found
not found
configure: error: wxWidgets is required. Try --with-wx-config.[/COLOR]
[COLOR=Blue]sam@Sam-ubuntu:~/EBInterface$[/COLOR] 

```

---

