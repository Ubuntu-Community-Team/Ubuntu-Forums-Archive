---
title: "Help, The second cpu wont work."
date: 2005-11-18
forum: General Help
---

### Post by warlock- on 2005-11-18
I got a problem,
I type in cat /proc/cpuinfo

and get:
oot@cs2-game:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 3
cpu MHz         : 2993.953
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5931.00

This means that the second one aint showing up, only one. So how do i get two to show up?
I got,
x2 - xeon intel 3.0 ghz 1mb cache

I run ubuntu aswell, Help please! :(

---

### Post by ebrowne on 2005-11-18
You'll have to install the smp kernel apt-get install linux-686-smp

---

### Post by warlock- on 2005-11-18
[QUOTE=ebrowne]You'll have to install the smp kernel apt-get install linux-686-smp[/QUOTE]
I get a error;
In swedish though, so i'll try to translate:
Seems like ubuntu cant get a list of the source-code or something. and that i have to type apt-get update, but after i do that and try again, it gives same error.

---

### Post by warlock- on 2005-11-18
Help :(!

---

### Post by warlock- on 2005-11-18
bump,
bump.

---

### Post by ebrowne on 2005-11-18
Check that you have the correct /etc/apt/source.list other than that I'm not sure.

---

