---
title: "Make intels acpi tool"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by the slayer on 2005-09-13
Hi i am trying to install intels acpi tool([http://developer.intel.com/technology/iapc/acpi/license2.htm](http://developer.intel.com/technology/iapc/acpi/license2.htm))
But when i try to type make, in the compiler, folder. Then i get this error:peter@ubuntu:~/knud/compiler$ make
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include    -c -o aslcompilerlex.o aslcompilerlex.c
aslcompiler.l: I funktionen 'comment':
aslcompiler.l:847: error: `yytext_ptr' undeclared (first use in this function)
aslcompiler.l:847: error: (Each undeclared identifier is reported only once
aslcompiler.l:847: error: for each function it appears in.)
make: *** [aslcompilerlex.o] Fejl 1
peter@ubuntu:~/knud/compiler$


Why wont make work? i works fine when i compile other things! I have buildessentiels installed.

---

