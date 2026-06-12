---
title: "Gutsy giving wierd CPU speed readings"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Pirate_Hunter on 2007-12-06
Hi like the title states my gutsy can't read my intel pentium 4 prescot 3.2Ghz properly, it reads my cpu as 2.80Ghz which is below its recommended spec. This is new to me as Feisty didn't do that so I'm wondering is there a way to fix this?

```
@LNX-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
[COLOR="Red"]cpu MHz[/COLOR]         : 2800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6404.53
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
[COLOR="Red"]cpu MHz[/COLOR]         : 2800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6400.74
clflush size    : 64

```

PS: the weird part is that when the cpu does reach 3.2Ghz it spikes and thats just annoying also I keep receiving cpu error when gutsy boots and it has to do with the actual cpu... something like "API error cpu not recognized/read properly", well it stays on screen for a short period of time so its hard to read it properly especially since part of it is a set of numbers. I hope that helps

---

### Post by Pirate_Hunter on 2007-12-08
o.0 I know most are on holiday this time of the month but hmmm... *BUMP*

Well just thought I should add one more piece of info, the weird message on boot that gutsy gives me is this:

```
MP-BIOS BUG: 8254 timer not connected to IO-APIC
```

Well I im 50% sure that explains the undercloak on my cpu but not certain, however if anyone has any kind of ideas that might help me fix this please do so.

---

### Post by Z_o-s-o on 2007-12-08
It's the speed stepping.

It can adjust the clock speed of the processor.

Mine does it as well.......800mhz - 1.6ghz - 2.0ghz.

It usually stays 800mhz while surfing and all that, but can be stepped up to 1.6 or 2.0ghz for more intense stuff.

---

### Post by Pirate_Hunter on 2007-12-09
^ I know but i use a desktop and dont have use for it still its nice to know that gutsy implemented it which is nice for laptop user etc but not for me especially when using virtual machines

Well after 2 days i figured out by talking in the debian channel "that was nerve rcking" :lolflag:

cutting the talk short just needed to use the command sudo /etc/init.d/powernowd stop than i needed to remove it from runlevels 2-5 ... which can be done with sysv-rc-conf (little console editor for startup scripts) or manually depending on the users preference.

---

### Post by simple_3 on 2007-12-09
```

user@ubuntu-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3010.946
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 6026.94
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 1
cpu MHz         : 3010.946
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl cid cx16 xtpr
bogomips        : 6021.77
clflush size    : 64

```
I have normally run with gutsy. May be you have to change cpu stepping to 1.

---

