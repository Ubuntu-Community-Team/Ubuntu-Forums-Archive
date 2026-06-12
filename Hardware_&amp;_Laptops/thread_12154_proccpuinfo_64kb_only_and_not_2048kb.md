---
title: "/proc/cpuinfo: 64kb only and not 2048kb"
date: 2005-01-22
forum: Hardware &amp; Laptops
---

### Post by zeno on 2005-01-22
Hi all,

i have one asus m6700n laptop with a Intel Centrino M-725 and when i do a cat command on /proc/cpuinfo i read this:

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 6
cpu MHz         : 1601.033
**cache size      : 64 KB**
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe tm2 est
bogomips        : 3170.30 

As u can read, ubuntu says that my processor has 64 kb only of cache but i'm sure that my processor has 2048kb of cache... do you know this problem?

Thanks,
zeno

---

### Post by LordGolem on 2005-01-22
Here the same on a CDC Premium 6764DW a laptop centrino based with 2MB L2 cache. 
cat /proc/cpuinfo is the same as zeno reported. 
What's wrong?

Davide

---

### Post by jerome bettis on 2005-01-22
same here, when i boot into the kernel that came with ubuntu, i noticed that cat proc/cpuinfo says 64kb cache.

but when i boot into the kernel that came with my laptop, it says 2048kb.  this kernel is soooo much faster, partially due to that i guess.

maybe try recompiling the kernel and see what happens, but i really don't know what you should do.

---

### Post by LordGolem on 2005-01-23
What kind of kernel came with your laptop?
What distribution and could you attach the config file of that kernel?
Is it possible also there is a boot kernel parameter the laptop manufacturer put there  and there isn't in ubuntu ?

---

### Post by Viro on 2005-01-23
The size of the cache reported by /proc/cpuinfo shouldn't have any bearing on performance. The cache is hardware based and is independent of the software running. If the cache is enabled, it will work regardless of the size being reported.

Incidently, this is a known problem with the Dothan family of Pentium M chips. Check out [http://tuxmobil.org/centrino.html](http://tuxmobil.org/centrino.html) for more details and notice that no one is too worried about the 64 KB of cache being reported. I wouldn't worry about it :)

---

### Post by LordGolem on 2005-01-23
Thankyou very much, Viro!

Bye
Davide

---

