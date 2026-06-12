---
title: "cannot find -lg2c"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by hersh on 2009-04-28
I m trying to use one software EIGNSOFT 3.0 for data analysis. 
When I am trying to install the software I am getting following error

[COLOR=Red]solid@ubuntu:~/t/src$ make all
mkdir -p  /home/solid/t/src/smartlib
mkdir -p  /home/solid/t/src/smarttables
mkdir -p  /home/solid/t/src/smartinclude
mkdir -p  /home/solid/t/src/../bin
cp  *.h  /home/solid/t/src/smartinclude
cp  eigensrc/*.h  /home/solid/t/src/smartinclude
cp  nicksrc/*.h  /home/solid/t/src/smartinclude
ar -r libnick.a strsubs.o sortit.o vsubs.o statsubs.o linsubs.o getpars.o xsearch.o gauss.o    gds.o
cp libnick.a  /home/solid/t/src/smartlib/nicklib.a
gcc -I/home/solid/t/src/smartinclude  -pthread -o smartpca smartpca.o  twsubs.o mcio.o qpsubs.o admutils.o egsubs.o regsubs.o eigsubs.o  eigx.o  /home/solid/t/src/smartlib/nicklib.a -L/usr/lib -lg2c -lm -llapack -latlas -lblas -Wimplicit 
/usr/bin/ld: cannot find -lg2c
collect2: ld returned 1 exit status
make: *** [smartpca] Error 1
solid@ubuntu:~/t/src$ [/COLOR]

[COLOR=Black]can anyone tell me how can i fix this error? and lg2c is required for what purpose

Thanks 
Hersh
[/COLOR]

---

### Post by borgene on 2009-10-29
I have the same problem. I assume that the libg2c0 package has to be installed.
I took a look at the Makefile, I think that atlan and blas will also need to be installed to get EIGENSOFT compiled.
(I can not yet report results, I'm fighting with a firewall.)

---

### Post by digitrev on 2009-10-29
I'm in the same boat. It seems that the upgrade to Koala uninstalled my nice shiny libg2c.s0.0 file. Another way to put it is

```
/usr/lib $ ll libg2c.s0
lrwxrwxrwx 1 root root 11 2009-09-30 14:12 libg2c.so -> libg2c.so.0

```

In other words, I now have a soft link pointing absolutely nowhere. Is this something I can fix?

---

### Post by fabio.hipolito on 2009-11-01
Hello,

I was facing the same problem with LAPACK and ARPACK libraries:

LAPACK error!

```
owl@owl-laptop:~/Master/Nanoribbons/ArmChair$ make
gfortran  -o aPROG -ffixed-line-length-120 ribbon.f -llapack 
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
make: *** [aPROG] Error 1
owl@owl-laptop:~/Master/Nanoribbons/ArmChair$
```

ARPACK error!

```
owl@owl-laptop:~/Master/ABchains/ABchainARPACK$ make
gfortran  -o aPROG -ffixed-line-length-120 linLattice.f -larpack 
/usr/bin/ld: cannot find -larpack
collect2: ld returned 1 exit status
make: *** [aPROG] Error 1
owl@owl-laptop:~/Master/ABchains/ABchainARPACK$
```

I followed advise from "hokim" at ubuntuforums thread "How to link lapack & blas?"

[http://ubuntuforums.org/showthread.php?t=70001&highlight=%2Fusr%2Fbin%2Fld%3A+find+-llapack]("http://ubuntuforums.org/showthread.php?t=70001&highlight=%2Fusr%2Fbin%2Fld%3A+find+-llapack")

where he recommend installing *-dev and *-headers (* stands for the library name) packages.

> **hokim said:**
> How about trying atlas3-base,atlas3-base-dev and atlas3-headers?
atlas3-headers  have  clapack.h but not  cblas.h which, I think, is missed.
But you can get cblas.h from 'sudo apt-get source atlas3-headers'

So open Synapatic or install via aptitude the following library:

```
liblapack-dev
```

this has a few dependecies, such as:

```
libblas-dev
libatlas-dev
...
```

and solved the LAPACK linking problem, in order to solve the ARPACK problem I installed:

```
libarapack-dev
```

and its respective dependencies.

It worked for me, hope it is usefull,
Best regards.

---

### Post by repettus on 2009-11-25
I also have this problem.
I tried 
cd /usr/lib
ln -s libg2c.so.0 libg2c.so from [http://www.linuxquestions.org/questions/linux-software-2/usrbinld-cannot-find-lg2c-654276/](http://www.linuxquestions.org/questions/linux-software-2/usrbinld-cannot-find-lg2c-654276/)

but no luck. Now this yields another error message"/usr/bin/ld: skipping incompatible /usr/lib64/libg2c.so when searching for -lg2c".

I am trying to compile RIP4 in Ubuntu 9.1 64 bit(grads metafile converter).

---

