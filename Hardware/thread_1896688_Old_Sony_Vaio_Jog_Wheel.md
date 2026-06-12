---
title: "Old Sony Vaio Jog Wheel"
date: 2011-12-17
forum: Hardware
---

### Post by Bozzer on 2011-12-17
I have been trying to get my Vaio jog wheel going for vol, bright etc.
It's a PCG-Z600 TEK. I have tried to install sjog-0.6, although it,s not in the repositories these days, so I tried the make install method.
When I do ./configure I get:

a@Vaio:~/sjog-0.6$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets ${MAKE}... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for X... no
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?
a@Vaio:~/sjog-0.6$ 


Info from sjog suggests kernel >2.4.x  well it is! (Lubuntu 10.10)
Same with above GTK version, >= 1.2.0   it is!

Is this a known issue? Would be nice to get going, espesh as Fn keys will turn volume up, but not down!

Have Googled this one loads but surprising little about it!

---

