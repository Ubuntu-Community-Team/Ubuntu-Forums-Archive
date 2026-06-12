---
title: "Hyperthread P4?"
date: 2005-11-28
forum: General Help
---

### Post by etlatino on 2005-11-28
does ubuntu support or I should say does the linux kernel support hyperthreading?

---

### Post by kosmic on 2005-11-28
Just install the i686-smp kernel

---

### Post by Leif on 2005-11-28
sudo apt-get install linux-686-smp, then reboot

---

### Post by sabitha on 2005-11-28
after that .... how we know that we have isntalled the right kernel for hypertrading.... i mean not the kernel but the hypertrading enable ;) 
sorry for my english

---

### Post by Leif on 2005-11-28
the smp stands for symmetric multiprocessing, which means it can handle multiple cpus, and hyperthreading. you just need to install it and choose it on boot (it will become the default anyway)

---

### Post by aminalshmu on 2005-11-28
look in /sys/devices/system/cpu/ for multiple cpu directories, or do
```
cat /proc/cpuinfo
``` and see if it returns more than 1 cpu.

---

### Post by sabitha on 2005-11-29
my computer have hypertrading but why only 1 processor show in cat /proc/cpuinfo
here's my cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model            : 3
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 4
cpu MHz        : 2869.153
cache size     : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug       : no
coma_bug      : no
fpu               : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 5668.86

my kernel is :
Linux ubuntu 2.6.10-5-686-smp #1 SMP Mon Oct 10 11:40:56 UTC 2005 i686 GNU/Linux

---

