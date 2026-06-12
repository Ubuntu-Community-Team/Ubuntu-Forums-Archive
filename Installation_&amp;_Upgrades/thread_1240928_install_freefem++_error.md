---
title: "install freefem++ error"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by permant on 2009-08-15
Hello :I want to install a software :freefem++,but there is something wrong with ubuntu 9.04(jaunty)
The readme file tell me:
./configure 
  make 
  make check    (to test de version)
  make install  (under root)
when I do that, it goes worng

permant@ubuntu:~$ cd freefem++-3.4-2/
permant@ubuntu:~/freefem++-3.4-2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for g77... no
checking for f77... no
checking for gfortran... no
checking for g77... no
checking for f90... no
checking for xlf... no
checking for xlf90... no
checking for fort77... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran 77 libraries of ... 
configure:  fatal error : no fortran  
configure: add ---without-fortran   
configure: or try to compile f2c in directory download/f2c   
configure:   just do:  make install  
configure: error:  Fatal error No Fortran compiler . 
permant@ubuntu:~/freefem++-3.4-2$ make
make: *** No targets specified and no makefile found.  Stop.
permant@ubuntu:~/freefem++-3.4-2$ 

So, how can I do ? and what's wrong?
thank you for your help !

---

### Post by Partyboi2 on 2009-08-15
Hi, looks like you need to install cfortran
```
sudo apt-get install cfortran
```

---

