---
title: "Zlib"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by AnimeKid on 2005-01-27
I was trying to compile a program using the ./configure command after I uncompressed it. I got this:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for nasm... no
checking for gzopen in -lz... no
configure: error: *** Cannot compile without zlib.

I'm new at Linux and I don't know what to do :( I think I have to uncompress zlib, but I don't know the code to do so... Thanks in advance

---

### Post by Matte on 2005-02-28
You can find a installation of Zlib in the package manager, just select to install it and it should work.

---

### Post by p!=f on 2005-02-28
You need the development package.
```

sudo apt-get install zlib1g-dev

```

---

