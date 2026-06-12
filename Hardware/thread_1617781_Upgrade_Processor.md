---
title: "Upgrade Processor?"
date: 2010-11-09
forum: Hardware
---

### Post by venicequeen7706 on 2010-11-09
I use the program Octave to make three dimensional graphs for teaching math, and I have found my computer doesn't handle it well. It seems to a lot of trouble when i try to change the angle i'm viewing from. A friend who knows a lot about MATLAB, which is a similar program, suggested its because of how old my processor is, so I was wondering if it would be a good solution to replace the processor.

 I'm using a compaq nc6230 with I believe an Intel celeron processor and 1.5 GB RAM. The computer is 4 years old, but I really never have problems except when doing complicated things in Octave or Freemat, so I don't want to buy a new computer if I don't have to.

Thanks.

---

### Post by 0N3 on 2010-11-09
Intel Celeron are one of the worst processors on the market. What socket number is your processor? Is it single core processor?

---

### Post by venicequeen7706 on 2010-11-09
I have no idea. I don't even know how to find that out actually. I got this info from running 'sudo lshw'

Intel(R) Pentium(R) M processor 1.86GHz version 6.13.8

---

### Post by 0N3 on 2010-11-09
open a terminal and type:

cat /proc/cpuinfo | grep -i Mhz

Post the output here.

---

### Post by venicequeen7706 on 2010-11-09
> **0N3 said:**
> open a terminal and type:

cat /proc/cpuinfo | grep -i Mhz

Post the output here.
'cat /proc/cpuinfo | grep -i Mhz'
cpu MHz        : 800.000

---

### Post by 0N3 on 2010-11-09
its a slow processor single core upgrading it is a big job if u don't know what your doing costly in a shop.

---

### Post by 0N3 on 2010-11-09
To explain it simple terms its the equivalent of a heart operation if you get what i mean.

---

### Post by venicequeen7706 on 2010-11-09
> **0N3 said:**
> To explain it simple terms its the equivalent of a heart operation if you get what i mean.
I see. Thanks.

---

### Post by JEDIDIAH on 2010-11-09
> **venicequeen7706 said:**
> I see. Thanks.

It's not that hard but you can destroy the machine if you are not careful. Getting the main PC apart will probably not be hard but CPU fans can be tricky. Dealing with the fan mount on my C2Q system was enough of a bother that I went with  spec-box-builder for my next machine after that.

---

