---
title: "Linux Question, Compiling"
date: 2008-10-10
forum: General Help
---

### Post by usul on 2008-10-10
Forgive me if this is a "dumb" question.

I read some where about improvements in performance
based on the target platform of the compiler.
Gentoo and Stampede Linux talk about this.

is Ubunto targeted for i383, would be faster is 
targeted to a faster cpu?

if it is better targeted is there a way to recompile
the kernal and software for the better system? 

A summary if you please but then if anyone know if any manuals documentation exist on this so I could educate myself a little better.

thank you in advance
usul
Please forgive this if I am asking this the wrong way or if its a stupid question.

---

### Post by jespdj on 2008-10-10
I think the 32-bit version of Ubuntu is targeted for i686.

Recompiling the kernel yourself for this reason is not recommended. The performance gain is most likely very minimal (so small you will most likely not notice anything), and strange problems and instability may occur when you're not using the "official" kernel for your Ubuntu distribution.

If you want better performance, especially in CPU-intensive applications, then a better idea is to use the 64-bit version of Ubuntu (if your processor is 64-bit capable; all newer AMD and Intel processors are). The speed difference for certain applications compared to the 32-bit version can be as high as 25%-30%.

---

