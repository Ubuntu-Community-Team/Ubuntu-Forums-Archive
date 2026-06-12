---
title: "complie error"
date: 2008-09-08
forum: General Help
---

### Post by boldexplorer on 2008-09-08
Hi I am trying to compile a programme for use on my computer. 
The programme is MIDAS a data acquisition programme. I have followed all the instructions on how to untar and then configure but when it comes time to make or compiling I get the following error:

cc -O -o example example.o -L. -lz
/usr/lib/gcc/i686-pc-linux-gnu/4.1.2/../../../../i686-pc-linux-gnu/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in ./libz.a(gzio.o)
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [example] Error 1

please can someone tell me what this means and what I am doing wrong.

Thanks!

---

### Post by manishtech on 2008-09-08
> /lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [example] Error 1

The compilation step succeeds but linking is failing... Check whether if you are using extern properly or not in the program if any?

---

