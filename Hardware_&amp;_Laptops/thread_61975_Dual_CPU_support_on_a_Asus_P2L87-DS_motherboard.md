---
title: "Dual CPU support on a Asus P2L87-DS motherboard"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by niw_uk1964 on 2005-09-02
I'm new to Linux and Ubuntu so please excuse me if the answers are obvious to you....

I've just installed Ubuntu 5.04 on a dual Pentium II 333 Asus P2L97-DS motherboard. On the terminal  typed:

cat /proc/cpuinfo

In return I get:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 3
cpu MHz         : 334.171
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 661.50

So, it appears that Ubuntu doesn't recognise the 2nd CPU even though the bios say it's there. Can anyone help?

TIA.

Nige.

---

### Post by niw_uk1964 on 2005-09-02
Fixed. Installed the dual processor kernel using synaptic manager.  :)

---

