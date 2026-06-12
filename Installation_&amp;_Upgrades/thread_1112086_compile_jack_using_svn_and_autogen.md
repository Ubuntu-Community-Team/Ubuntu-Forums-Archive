---
title: "compile jack using svn and autogen"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by leighgable on 2009-03-31
Hello,

Im having trouble compiling the latest jack version on my ubunto intrepid variant. Autogen output looks promising (see below), but i don't get any of the build messages, and then when it stops, Make returns a "no target or makefile" error.

Any ideas?


leigh@tiny:~/jack$ sudo ./autogen.sh --prefix=/usr --with-default-tmpdir=/dev/shm
[sudo] password for leigh: 
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: linking file `config/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: linking file `m4/libtool.m4'
libtoolize: linking file `m4/ltoptions.m4'
libtoolize: linking file `m4/ltsugar.m4'
libtoolize: linking file `m4/ltversion.m4'
libtoolize: linking file `m4/lt~obsolete.m4'
configure.ac:53: installing `config/config.guess'
configure.ac:53: installing `config/config.sub'

leigh@tiny:~/jack$ ls
acinclude.m4                   config.log    example-clients  Makefile.in
aclocal.m4                     configure     jack             man
AUTHORS                        configure.ac  jackd            README
autogen.sh                     COPYING       jack.pc.in       README.developers
autom4te.cache                 COPYING.GPL   jack.spec.in     TODO
BUILDING-FOR-LINUX-2.4-KERNEL  COPYING.LGPL  libjack          tools
config                         doc           m4
config.h.in                    drivers       Makefile.am

---

### Post by leighgable on 2009-04-19
It was missing dev versions of the necessary libraries that was tripping me up. 

sudo aptitude install libsamplerate0-dev libasound2-dev libsndfile1-dev libncurses5-dev libreadline5-dev
and if you want the FireWire support:
sudo aptitude install libfreebob0-dev

That allowed me to compile. Hope that helps someone, someday.

Best, Leigh

---

