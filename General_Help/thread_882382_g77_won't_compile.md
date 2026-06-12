---
title: "g77 won't compile"
date: 2008-08-06
forum: General Help
---

### Post by pr4wn on 2008-08-06
hi,

i've been trying to compile some fortran codes on my machine. and keep running into the same error message:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

i tried to run it in verbose, but haven't found any clues here:

$ g77 -v fhn2d_cp5.f 
Driving: g77 -v fhn2d_cp5.f -lfrtbegin -lg2c -lm -shared-libgcc
Reading specs from /usr/lib/gcc/i486-linux-gnu/3.4.6/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --with-tune=pentium4 i486-linux-gnu
Thread model: posix
gcc version 3.4.6 (Ubuntu 3.4.6-6ubuntu2)
 /usr/lib/gcc/i486-linux-gnu/3.4.6/f771 fhn2d_cp5.f -quiet -dumpbase fhn2d_cp5.f -mtune=pentium4 -auxbase fhn2d_cp5 -version -o /tmp/ccWzwcDg.s
GNU F77 version 3.4.6 (Ubuntu 3.4.6-6ubuntu2) (i486-linux-gnu)
        compiled by GNU C version 3.4.6 (Ubuntu 3.4.6-6ubuntu2).
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
 as --traditional-format -V -Qy --32 -o /tmp/ccTpSOsi.o /tmp/ccWzwcDg.s
GNU assembler version 2.18 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.18
 /usr/lib/gcc/i486-linux-gnu/3.4.6/collect2 --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 crt1.o crti.o /usr/lib/gcc/i486-linux-gnu/3.4.6/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib /tmp/ccTpSOsi.o -lfrtbegin -lg2c -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/i486-linux-gnu/3.4.6/crtend.o crtn.o
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

i can't really tell what's going on by looking at the /usr/bin/ld file. 
reinstalling different versions of g77 through synaptic did no good either. i tried using gcc instead, but get a different error: 

gcc: error trying to exec 'f951': execvp: No such file or directory
 
i'm sure the problem is not in the code itself because i just compiled it fine on my network machine at school. 

any help would be greatly appreciated.

regards,

pr4wn

---

### Post by RHAnthony on 2008-08-22
I'm getting the same errors trying to compile Kismet and I'm being told it's a missing library or two, but I can't find any way to get them installed so that Kismet can compile.  Doesn't help that I'm not all that fluent in compiling stuff yet either.

If I find an answer to my issue I'll post here and hopefully it will help you as well.

---

### Post by stonehenge on 2008-09-04
Yep, same issue here.  Tried compiling with the following line:
gcc -o testfor testfor.f95

and I get the following error:

gcc: error trying to exec 'f951':execvp: No such file or directory

gcc is installed (?) and doing "man gcc" says I should be able to compile fortran code.

Any help from Ubuntu gurus would be welcomed

Or should I convert to another linux package like Fedora or Suse?

---

### Post by singh.gurjeet on 2008-09-05
Follow this thread... I am just following it right now, so can't say if it will work for me!

---

### Post by singh.gurjeet on 2008-09-05
Sorry, I forgot to post the URL.

[http://ubuntuforums.org/showthread.php?t=190193](http://ubuntuforums.org/showthread.php?t=190193)

This worked for me..

---

### Post by pr4wn on 2009-04-01
alright, that works. the only snag was i had to reburn my ubuntu 7.10 install disk to install the libc6-dev package, but after that things ran smoothly. 

thank you very much! :D

---

