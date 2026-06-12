---
title: "Foomatic-rip 4.0 installation"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by niivethitha on 2009-01-23
Hi,

I am trying to install foomatic-rip 4.0.

It is giving following error wen i do...

./configure – ran successfully

Make – (to install)

bash-3.00# make
make  all-am
source='process.c' object='process.o' libtool=no \
DEPDIR=.deps depmode=none /bin/bash ./depcomp \
gcc -DHAVE_CONFIG_H -I. -I. -I.  -DCONFIG_PATH='"/usr/local/etc/foomatic"'    -g
 -O2 -c process.c
source='renderer.c' object='renderer.o' libtool=no \
DEPDIR=.deps depmode=none /bin/bash ./depcomp \
gcc -DHAVE_CONFIG_H -I. -I. -I.  -DCONFIG_PATH='"/usr/local/etc/foomatic"'    -g
 -O2 -c renderer.c
renderer.c: In function `jcl_keywords_equal':
renderer.c:156: warning: assignment makes pointer from integer without a cast
renderer.c:162: warning: assignment makes pointer from integer without a cast
renderer.c: In function `exec_kid4':
renderer.c:287: warning: initialization makes pointer from integer without a cas
t
source='fileconverter.c' object='fileconverter.o' libtool=no \
DEPDIR=.deps depmode=none /bin/bash ./depcomp \
gcc -DHAVE_CONFIG_H -I. -I. -I.  -DCONFIG_PATH='"/usr/local/etc/foomatic"'    -g
 -O2 -c fileconverter.c
gcc  -g -O2   -o foomatic-rip  foomaticrip.o options.o  pdf.o postscript.o util.
o  spooler.o process.o renderer.o  fileconverter.o  -lm
ld: fatal: symbol `printer_model' has differing sizes:
        (file foomaticrip.o value=0x80; file options.o value=0x100);
        tentative symbol cannot override defined symbol of smaller size
ld: fatal: File processing errors. No output written to foomatic-rip
collect2: ld returned 1 exit status
*** Error code 1
make: Fatal error: Command failed for target `foomatic-rip'
Current working directory /opt/foo-4.0/foomatic-filters-4.0.0
*** Error code 1
make: Fatal error: Command failed for target `all'

Please let me know how to solve the error.

Thanks in advance.

---

