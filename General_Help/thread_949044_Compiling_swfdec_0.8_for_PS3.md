---
title: "Compiling swfdec 0.8 for PS3"
date: 2008-10-15
forum: General Help
---

### Post by 9a3eedi on 2008-10-15
Hi,

I'm running Ubuntu 7.10 on the PS3 (powerpc). Since powerpc has no flash, I was trying to get swfdec to work for ubuntu. But the one in the repos are just too old, and gnash is unusuable.. so I decided to get the source tarball and compile it myself. I'm stuck at the ./configure point:

```

the9a3eedi@localhost:~/tar/swfdec-0.8.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for supported compiler flags...  -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -Wold-style-definition -Wdeclaration-after-statement -Wmissing-declarations -Wmissing-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Winline -Wformat-nonliteral -Wformat-security -Wswitch-enum -Wswitch-default -Winit-self -Wmissing-include-dirs -Wundef -Waggregate-return -Wmissing-format-attribute -Wno-multichar -Wnested-externs
configure: WARNING: unsupported compiler flags:  -Waddress
./configure: line 3549: AM_PROG_LIBTOOL: command not found
checking for supported compiler flags...  -std=gnu99
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for timezone support... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... no
configure: error: glib-2.0, gobject-2.0 and gthread-2.0 >= 2.16 are required to build swfdec
the9a3eedi@localhost:~/tar/swfdec-0.8.0$ 


```

I couldn't find the packages its talking about in the repos. And I'm pretty sure glib is installed in some form in ubuntu. I mean doesn't ubuntu depend on glib? Also I couldn't find any useful guides on the internet for compiling this version of swfdec.. so..

Can anybody help me out?

---

### Post by Partyboi2 on 2008-10-16
Have you tried  libglib2.0-dev

---

### Post by Yellow Pasque on 2008-10-16
Try this command. It may not get all the packages you need to build the latest version, but it should get all the packages needed to build the version in the repo (i.e. it will at least get you close)
```
sudo apt-get build-dep libswfdec0.5-1
```

---

### Post by 9a3eedi on 2008-10-29
^ I tried doing that, but I still get the error during ./configure

> **Partyboi2 said:**
> Have you tried  libglib2.0-dev

I tried. I still get the error >_>



atm I'm trying to look for a binary

---

### Post by doidoi on 2008-11-01
Its about versions ... gutsy uses glib 2.14 and swfdec 0.8 needs 2.16.
glib 2.16 is introduced in hardy, which is not available for powerpc architecture. I am almost sure that it is possible to compile glib 2.16 for gutsy ppc. But i know swfdec 0.8 will need other packages which are not present in gutsy. (i think those also could be be compiled)

You can try my [sarge compilation]("http://doidoi.extra.hu/debian/index.html") for libglib.

---

