---
title: "What Kernel to choose!?"
date: 2004-12-31
forum: Hardware &amp; Laptops
---

### Post by telmo on 2004-12-31
Hello my friends! :)

I have currently two computers with two different processors. I have a Pentium 4 3.06Ghz with no Hyper-Threading (Thieves!) and a AMD Mobile 2600+.

So... wich Kernel should i use? i386 or i686? And should i use 'smp' or not?

THX  8-[

---

### Post by safecracker on 2004-12-31
i686 is optimized for the pentium chip and i386 means that it will work on any x86 machine which is 386 and upwards. This includes 486, pentium, pentium, pentium 3 etc, but is not optimized to your specific chip just generalized.

---

### Post by clsdaniel on 2004-12-31
Depends very much on your architecture, but in general here:

i386: All machines from 386 upwards that are x86 of course, this includes, 386, 486, pentiums 1, 2, 3, 4, celerons and all AMD chips, as well cyrix chips and transmeta.

i586: Very different than vanilla i386, this is optimized from pentium onwards, and includes some pentium clones from cyrix and celerons from first generation onwards, and all AMD i think.

i686: Basically pentium pro, pentium 2, 3, 4 and celerons as well most AMD from k6.

K7: Optimized for K7 AMD procesors, this ones are from Athlon onwards.

smp: optimized for multiple processor architecture, his includes xeons, dual pentiums, dual athlons (athlon mp), dual opertron, etc. As well pentium 4 with hyper threading.

This covers rougly most architecture optimizations for the different kernels on ubuntu.

---

### Post by telmo on 2005-01-01
Thank you very much! ;)

---

