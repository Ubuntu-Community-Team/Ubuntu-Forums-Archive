---
title: "Dual CPU"
date: 2006-05-20
forum: Hardware &amp; Laptops
---

### Post by henry95 on 2006-05-20
Hey everyone!  

I need some help configuring ubuntu to see both CPU's . I know i need an SMP kernel, but i'm not sure how I can search and install it for ubuntu, I have re-compiled the kernel before so I don't need help there.  I just don't know if their is an ubuntu specific kernel that I should get with apt-get.

Machine Info:
ASUS NCCH-DL Dual Socket 603/604 Intel 875P ATX Server Motherboard
2x 3.2 Intel Xeon.

Here is /proc/cpuinfo if needed.

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 3.20GHz
stepping        : 5
cpu MHz         : 3208.249
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6356.99

```

-Thanks!

---

### Post by henry95 on 2006-05-20
I got it!

haha I should of messed around before posting.

I clicked System--->Administration--->Synaptic Pacage Manager.

I then searched for SMP and just installed it.  Wasy very easy.

Another thumbs up to ubuntu to making life a little easier :)

---

