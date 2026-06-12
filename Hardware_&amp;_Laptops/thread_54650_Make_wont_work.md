---
title: "Make wont work"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by Peter84 on 2005-08-05
Hi I just installed ubuntu on my acer travelmate 2303lc. All went well. But i need til compile intels tool for acpi support to get my battery working. But when i type make, there is an error:
[email]root@ubuntu:/home/peter/acpica-unix-20050624.tar.gz[/email]_FILES/acpica-unix-20050624/compiler # make
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include -c -o aslcompilerlex.o aslcompilerlex.c
aslcompiler.l: I funktionen 'comment':
aslcompiler.l:847: error: `yytext_ptr' undeclared (first use in this function)
aslcompiler.l:847: error: (Each undeclared identifier is reported only once
aslcompiler.l:847: error: for each function it appears in.)
make: *** [aslcompilerlex.o] Fejl 1
What does it mean???
Ive installe build.essential. g++ c++ c. And everything else i could think of

---

### Post by vedran on 2005-10-01
You need build-essential and flex, or maybe flex-old

---

### Post by titan21 on 2005-10-03
Hello,

Am having a similar problem. Need flex to compile PHP on Ubuntu, but can't seem to find it in the repositories. Is this what i should be using or is there somewhere I can get a copy of something to do the same job?

Thanks in advance,

Tim

---

