---
title: "[SOLVED] Please help! libxfcegui4-3 wants to uninstall Xfce4"
date: 2008-07-13
forum: General Help
---

### Post by dodle on 2008-07-13
I have added to following repositories to my Xubuntu install:> deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing mainI did this because I would like to be able to install xfce4-panel-menu.  When I go into synaptic and attempt to install it, and error message comes up.  The attachment shows the error.  So I go ahead and try to install libxfce4mcs-client-2 and the others, but when I do so is says:> To Be Removed:
   xubuntu-desktop
   thunar
   xfwm
   xfce4-session
   (etc.)It wants to completely remove my Xfce4 desktop.

Also, (for example) when is says that I need to install libxfcegui4-3, I already have libxfcegui4-4 installed.  The others are the same:  For libxfce4mcs-client-2, there is already installed libxfce4mcs-client3.  Please help, I would really like to have the xfce4-panel-menu plugin.

---

### Post by ghost_ryder35 on 2008-07-13
you could download it from this site
[http://developer.berlios.de/projects/xfce4panelmenu/](http://developer.berlios.de/projects/xfce4panelmenu/)

direct download:
[http://developer.berlios.de/project/showfiles.php?group_id=3138&release_id=5576](http://developer.berlios.de/project/showfiles.php?group_id=3138&release_id=5576)

---

### Post by dodle on 2008-07-13
I did actually try that first, and I used alien to create a .deb package out of the source package.  But after installation it didn't show up under "Add Items to the Panel".  I didn't try to compile it from the source because I have bad luck about 50% of the time with that.  I guess I will try compiling it though, it's worth a shot.

---

### Post by ghost_ryder35 on 2008-07-13
yea make sure you have "build-essential" installed u will need it
usually compiling goes like this

make
make install

do read the readme once u un tar the package

---

### Post by dodle on 2008-07-13
Well, I tried to install from source.  ./configure seemed to work fine, but then when I used "make" I get "no targets specified and no makefile found".  Any ideas?  Here is what "./configure brings up:> root@moms:/opt/xfce4-panel-menu-plugin-0.3.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for dbh-1.0... root@moms:/opt/xfce4-panel-menu-plugin-0.3.1# make
make: *** No targets specified and no makefile found.  Stop.
root@moms:/opt/xfce4-panel-menu-plugin-0.3.1# 


---

### Post by voteforpedro36 on 2008-07-13
1. Do you have the package "build-essential" installed?

2. You shouldn't add Debian repos to Ubuntu, just a bad idea in general.

---

### Post by dodle on 2008-07-13
Yes, I have "build-essential" installed.

---

### Post by dodle on 2008-07-14
xfce4-panel-menu is trying to install older versions of libxfce4mcs-client, libxfce4mcs-manager, libxfce4util, and libxfcegui.  Is there a way to make symbolic links for these and "trick" xfce4-panel-menu into thinking they are the older versions?

---

### Post by dodle on 2008-07-14
Does anyone have a resolution for the following issue I am having?[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77666&d=1215996468[/IMG]

---

### Post by ghost_ryder35 on 2008-07-14
isnt this the same thread as [http://ubuntuforums.org/showthread.php?t=858704](http://ubuntuforums.org/showthread.php?t=858704)
i take it compiling didnt work?

---

### Post by ghost_ryder35 on 2008-07-14
i think in order for this to work you would have to install all the debian repos.... but that would screw things up nicely.  so just download the .deb package from the ubuntu site.

[http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel-menu-plugin/](http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel-menu-plugin/)

direct download:
[http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel-menu-plugin/xfce4-panel-menu-plugin_0.2.2-1ubuntu2_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel-menu-plugin/xfce4-panel-menu-plugin_0.2.2-1ubuntu2_i386.deb)

---

### Post by dodle on 2008-07-14
I get the same error with the .deb as I do when trying to install from Synaptic.

---

### Post by dodle on 2008-07-14
Well, I'm giving up on this.  Thanks for your help everyone.

---

### Post by dodle on 2008-07-14
I'm giving up on this.

---

### Post by bapoumba on 2008-07-15
Threads merged.
This is usually what happens when you use non-ubuntu repos in your sources.list, you get dependencies problems.
The distribution and dependencies are coherent within a release, not between several releases, and of course not between several distros :)

---

