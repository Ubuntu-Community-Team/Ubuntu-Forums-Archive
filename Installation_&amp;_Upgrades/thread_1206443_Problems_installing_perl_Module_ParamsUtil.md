---
title: "Problems installing perl Module Params::Util"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by dominics on 2009-07-07
Hi, 

I am trying to install Params::Util on jaunty installation via CPAN, but it keeps failing.

Here is the output :

Writing Makefile for Params::Util
cp lib/Params/Util.pm blib/lib/Params/Util.pm
/usr/bin/perl /usr/share/perl/5.10/ExtUtils/xsubpp  -typemap /usr/share/perl/5.10/ExtUtils/typemap  Util.xs > Util.xsc && mv Util.xsc Util.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"1.00\" -DXS_VERSION=\"1.00\" -fPIC "-I/usr/lib/perl/5.10/CORE"  -DPERL_EXT Util.c
/bin/sh: cc: not found
make: *** [Util.o] Error 127
  ADAMK/Params-Util-1.00.tar.gz
  make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 ADAMK/Params-Util-1.00.tar.gz                : make NO

Any ideas what the issue may be?

---

### Post by dominics on 2009-07-07
Doh! after further investigation, I realised it needed a C Compiler and once I installed CCbuild, Params::Util installed without issues.

---

