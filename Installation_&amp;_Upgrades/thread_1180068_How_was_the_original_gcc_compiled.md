---
title: "How was the original gcc compiled?"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-06-06
I was just wondering how they compiled the original gcc?

---

### Post by benj1 on 2009-06-06
heres the answer
[http://en.wikipedia.org/wiki/Bootstrapping_(compilers)]("http://en.wikipedia.org/wiki/Bootstrapping_(compilers)")


although existentialists et al may have other suggestions

---

### Post by Matt Yun on 2009-06-06
GCC compiled itself:  [http://gcc.gnu.org/wiki/History](http://gcc.gnu.org/wiki/History)

Wikipedia: [http://en.wikipedia.org/wiki/GCC](http://en.wikipedia.org/wiki/GCC)

---

### Post by night_fox on 2009-06-06
I dare say gcc was originally compiled with another c compiler.

The first c compiler would have to have been written in something else, like assembly language, and the first assembler would have had to be written in pure machine code, but it was probably for a machine with simple instructions. That would have made the assembly language easier, so you could have written a c compiler more easily.

gcc takes preprocessed c and produces assembly language. when asked to do anything else, it calls cpp (preprocessor), as (assembler), and ld (linker). The last two are in a package call binutils.

This tells you how to compile it. Some parts can only be built in gcc
[http://gcc.gnu.org/install/build.html](http://gcc.gnu.org/install/build.html)

It tells you how to build a cross compiler and a native compiler. To build a native compiler, gcc compiles itself', uses itself' to compile itself'' and uses itself'' to compile itself'''. It then makes sure itself'' is itself'''.

To build a compiler on another machine (target), you have to have a native compiler on your machine (host), then use that to cross compile gcc for the target machine. Then you have to move cross compiled gcc to the target machine and use it to compile a native gcc

---

### Post by benj1 on 2009-06-06
i think the lisp compiler is my favourite, they already had an interpreter before they had a compiler, so they wrote the compiler in lisp then they ran the compiler through the compiler through the interpreter.

---

