---
title: "Processor slower than it should be?"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by Old Pink on 2006-10-25
Hi all.

I've known this ever since I started using Ubuntu, but haven't felt ready enough to face it yet really. 

Here's the problem:
> matt@matt-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping        : 7
cpu MHz         : 1992.089
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
bogomips        : 3988.44As you can see, I have a 2.66Ghz processor, which ran that fast in Windows, but in Ubuntu I only get 1992.089Mhz (1.9/2.0GHz)

Where are my extra 660Mhz? I don't miss them all that much, my system runs like a dream, but I'd like to know if there's a reasoning behind it? 

BIOS etc. states the processor to be a 2.66Ghz one...

---

### Post by po0f on 2006-10-25
Old Pink,

Do you have a CPU throttling daemon running in the background?  Check /proc/cpuinfo after your box has been idle a while, then do some stuff non-trivial stuff (open up OO.o) and re-check it.  Hopefully the speed will throttle back up.

---

### Post by Old Pink on 2006-10-25
Thanks, but I don't think it's an issue like that for some reason. 

It just doesn't seem temporary/variable. :S

---

