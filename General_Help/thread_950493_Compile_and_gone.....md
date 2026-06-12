---
title: "Compile and gone...."
date: 2008-10-17
forum: General Help
---

### Post by peugas on 2008-10-17
Hi everyone,

I've been using Ubuntu for two years and after reading a lot of Q/A in this forum, I found that it's my time to be the one to ask a question!

today I compile a program in my terminal using
```
gcc -ansi -pedantic -Wall -o sock001.c sock001
```
(I know it's wrong, it should be the *.c in the last)

and I got this output from the terminal:
```
sock002: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.text+0x0): first defined here
sock002:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
sock002: In function `_fini':
/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o:/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: first defined here
sock002:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
sock002: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.data+0x0): first defined here
sock002: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.2.3/crtbegin.o:(.data+0x0): first defined here
sock002: In function `_init':
/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o:/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:15: first defined here
collect2: ld returned 1 exit status
```

Then I found that my C program disappeared!
Two questions:
[LIST=1]
[*]Why have this happenned?
[*]where can my file be?
[/LIST]

just in case, the program is a regular and simple server socket program.
the problem is if this happen with a more complex program.

I'm using Ubuntu 8.04-Hardy Heron on an ASUS laptop

Thank you everyone

---

