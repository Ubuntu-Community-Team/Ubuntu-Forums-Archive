---
title: "Need a good FLOPS benchmark program"
date: 2008-10-19
forum: General Help
---

### Post by ukeitaro on 2008-10-19
I've been implementing a very intensive computational algorithm.  For the moment, I'll be profiling my program's performance on my personal Ubuntu system (8.04, 64-bit).  Of course, how fast my program runs will depend on my specs: CPU, memory, etc.  To get a better understanding of how fast the program runs, I'd like to benchmark my computer and have an estimate of its maximum FLOPS.  

Do you know of any good benchmarks that can calculate your system's FLOPS?

Thanks!

---

### Post by clubsoda on 2008-11-20
Try [nbench]("http://www.tux.org/~mayer/linux/bmark.html")
I haven't found a deb package of this so you have to "tar -xvf" and "make" it first.  Also, it doesn't output FLOPS per se, rather a benchmark relative to an AMD K6 233MHz.

I gave it a go.  My machine scored as follows:-

MEMORY INDEX        : 2.596
INTEGER INDEX       : 2.748
FLOATING-POINT INDEX: 4.238

Impressive, eh? ;)

---

### Post by JFekete9076 on 2011-04-18
Here is my result:
```

BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1395.6  :      35.79  :      11.75
STRING SORT         :          218.48  :      97.62  :      15.11
BITFIELD            :       5.568e+08  :      95.51  :      19.95
FP EMULATION        :          411.84  :     197.62  :      45.60
FOURIER             :           32687  :      37.17  :      20.88
ASSIGNMENT          :          37.875  :     144.12  :      37.38
IDEA                :          5821.7  :      89.04  :      26.44
HUFFMAN             :          2577.9  :      71.49  :      22.83
NEURAL NET          :          51.559  :      82.83  :      34.84
LU DECOMPOSITION    :          1576.7  :      81.68  :      58.98
==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 93.072
FLOATING-POINT INDEX: 63.119
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : 4 CPU AuthenticAMD AMD Athlon(tm) II X4 640 Processor 3000MHz
L2 Cache            : 512 KB
OS                  : Linux 2.6.35-28-generic
C compiler          : gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
libc                : libc-2.12.1.so
MEMORY INDEX        : 22.419
INTEGER INDEX       : 23.849
FLOATING-POINT INDEX: 35.008
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38

```

I don't understand why this program works with only one CPU. I was watching the CPU usage meter during runtime. Is there such a benchmark optimized for multicore CPUs?

---

### Post by RoyLongbottom on 2011-04-27
[FONT=Verdana]Try some of mine[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana][http://www.roylongbottom.org.uk/linux%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20benchmarks.htm) [/FONT]
[FONT=Verdana][http://www.roylongbottom.org.uk/linux%20burn-in%20apps.htm](http://www.roylongbottom.org.uk/linux%20burn-in%20apps.htm) [/FONT]
 
Roy

---

### Post by clubsoda on 2011-05-04
> **JFekete9076 said:**
> I don't understand why this program works with only one CPU.Here's a dual-core version```
./nbench & ./nbench
```You have to add up the results. There will be a quad-core version too, currently under heavy development.:D
Seriously though, nbench dates back to 1995 and was written for consumer desktops of that time. Single threaded.

[quote=RoyLongbottom]Try some of mine[/quote]Wow, that's an impressive set of utilities you've got there. I was wondering what the licensing status of those Compuserve posts would be and whether there's any possibility that your code could be packaged as a .deb under the GPL(?) I guess like nbench they should be distributed as source though, as it might not be fair to benchmark a machine using code compiled and optimized for a different machine.

Cheers.

---

### Post by RoyLongbottom on 2011-05-17
Source code is included in tar.gz files - FREE - anyone can use them

---

### Post by xclusive585 on 2012-03-12
Curious, did anyone package any of those utilities into a .deb yet? or is this gonna be the ONE that I learn to compile with/for...? :-)

---

