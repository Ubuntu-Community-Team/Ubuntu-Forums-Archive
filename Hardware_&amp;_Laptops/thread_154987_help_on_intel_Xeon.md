---
title: "help on intel Xeon"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by mrpivello on 2006-04-04
Hi, we're having a problem with installing ubuntu 5.10 for an intel Xeon with 4 32 bits processors. Although we have 8 GB RAM, and the system finds it, we can't get it to manage more than 3.3 Gb. Is there a way to make it manage the other 5Gb? Or, on the other hand, since it has 4 processors, is there a way to make multiple boots and each one get its own 3Gb and run independently and its own processor?

Thanks In Advance

-Márcio Ricardo

---

### Post by kosmic on 2006-04-04
What is the Kernel you are using ? the 386 ?? to use more than 3.3GB of memory you need to use the 686 kernel :)

---

### Post by mrpivello on 2006-04-05
We are using the 686 kernel. Is there any special flag or something that we should set? Does this kernel recognize automatically the Xeon processor? What must be done for the kernel to manage more than 3.3GB?

TIA

-Márcio Ricardo

---

### Post by mox on 2006-04-05
exactly which it is the kernel that it uses? 

mox

(I have many problem wiyh a dual xeon 2Gh 32bit; every time kernel panic with smp and/or 686 kernel)

---

### Post by mrpivello on 2006-04-06
in the first boot option of grub (menu.lst) it is listed 2.6.12, but bellow there is 2.6.12-10-686-smp. It means that it is running the first option, doesn't it?

---

### Post by mox on 2006-06-13
Finally!!!!!

Dapper;

uname -r
2.6.15-23-686

cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) XEON(TM) CPU 2.00GHz
stepping        : 4
cpu MHz         : 2000.173
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 4002.92

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) XEON(TM) CPU 2.00GHz
stepping        : 4
cpu MHz         : 2000.173
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3998.84

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) XEON(TM) CPU 2.00GHz
stepping        : 4
cpu MHz         : 2000.173
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3998.91

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) XEON(TM) CPU 2.00GHz
stepping        : 4
cpu MHz         : 2000.173
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3999.00

:D

---

