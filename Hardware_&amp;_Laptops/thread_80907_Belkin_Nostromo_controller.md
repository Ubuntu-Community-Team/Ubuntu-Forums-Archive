---
title: "Belkin Nostromo controller"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by riotnerd on 2005-10-23
I am unable to complie the nostromo software [http://sourceforge.net/projects/nostromodriver/]("http://sourceforge.net/projects/nostromodriver/") without "undefined reference to `pthread_create'" errors.  It works fine on the Xandros 3.

**./confiure without errors:**
[INDENT]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) gawk
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
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
debugging disabled
checking for fltk-config... /usr/local/bin/fltk-config
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers 
checking for egrep... grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for NOSTROMO_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2  
checking for NOSTROMO_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lxml2 -lz -lm  
checking for XTestFakeKeyEvent in -lXtst... yes
checking for an ANSI C-conforming const... yes
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: executing depfiles commands

[/INDENT]
**make gives errorrs**
[INDENT]
ui.cxx: In function ‘void cb_key_repeat_delay_input(Fl_Value_Input*, void*)’:
ui.cxx:233: warning: passing ‘double’ for argument 1 to ‘void change_key_repeat_delay(int, int, int)’
daemon.o: In function `spawn_reader(int, int)':
daemon.cxx:(.text+0x2469): undefined reference to `pthread_create'
daemon.o: In function `main':
daemon.cxx:(.text+0x27c8): undefined reference to `pthread_create'
daemon.cxx:(.text+0x28b4): undefined reference to `pthread_create'
daemon.cxx:(.text+0x28f3): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
make[2]: *** [nostromo_daemon] Error 1
make[1]: *** [all] Error 2
make: *** [all-recursive] Error 1[/INDENT]

---

