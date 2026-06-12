---
title: "cpu frequency scaling monitor"
date: 2010-05-13
forum: Hardware
---

### Post by kakao2 on 2010-05-13
I found how to change the processor speed of my Eee PC 701. It is modprobe p4-clockmod. Before the change it runs at 630 MHz and after at 900 MHz and I can change the cpu frequency with the  applet to any of 900, 787, 675, 562, 450, 337, 225, 112 MHz.  How to make the change permanent? Or better yet, to make it vary on demand?
```

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor          900MHz
stepping    : 8
cpu MHz        : 630.181
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips    : 1260.36
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

``````
# modprobe p4-clockmod
``````

 cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor          900MHz
stepping    : 8
cpu MHz        : 900.000
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips    : 1260.36
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

```

---

### Post by kakao2 on 2010-05-13
The answer is: install cpufreqd package

---

### Post by kalehrl on 2012-11-18
I've just got a used eee pc 701 4g laptop and after
```
modprobe p4-clockmod
```
the
```
cat /proc/cpuinfo
```
reports 900MHz but in fact it is false because CPU runs at a stock 630MHz.
I ran this
```
time echo "scale=1500; 4*a(1)" | bc -l
```
and there is no difference when using 900MHz or 630MHz speeds.

---

### Post by wildmanne39 on 2012-11-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

