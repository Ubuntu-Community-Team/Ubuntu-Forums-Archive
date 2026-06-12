---
title: "Problem with installing gcc-4.3.3"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by runningpig001 on 2009-02-08
Hi,

I want to run a fortran program with my laptop. Should I install gcc first?

I downloaded the gcc-4.3.3 package and extracted it.

Following the instructions in [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I finished the background part.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Then I ran: ./configure
result:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gnatbind... no
checking for gnatmake... no
checking whether compiler driver understands Ada... no
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for correct version of gmp.h... no
configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+.
Try the --with-gmp and/or --with-mpfr options to specify their locations.
Copies of these libraries' source code can be found at their respective
hosting sites as well as at [ftp://gcc.gnu.org/pub/gcc/infrastructure/](ftp://gcc.gnu.org/pub/gcc/infrastructure/).
See also [http://gcc.gnu.org/install/prerequisites.html](http://gcc.gnu.org/install/prerequisites.html) for additional info.
If you obtained GMP and/or MPFR from a vendor distribution package, make
sure that you have installed both the libraries and the header files.
They may be located in separate packages.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
then I ran: make
result:

make: *** No targets specified and no makefile found.  Stop.


so, what is problem? Any suggestion is really appreciated!!!

---

### Post by snova on 2009-02-08
You don't need to compile anything.

If you're just running the Fortran program, you might not need to do anything at all.

If it's not working, try installing the **gfortran** package through Synaptic.

---

### Post by runningpig001 on 2009-02-08
> **snova said:**
> You don't need to compile anything.

If you're just running the Fortran program, you might not need to do anything at all.

If it's not working, try installing the **gfortran** package through Synaptic.

it works, thank you!

---

