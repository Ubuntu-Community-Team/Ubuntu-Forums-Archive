---
title: "Ubuntu shows wrong processor - T7400 Merom on Inspiron 6400"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by CSISagent on 2007-05-19
This was the same on Edgy, now also occurring on Feisty after the upgrade. It seems that the Hardware Information Utility, and the results of the command below show my processor as a T2600 rather than a T7400 Merom which it actually is. 

The CPU frequency is correct, but the FSC is not (merom has 4MB of FSC). I don't know if this is hampering performance or not, or if I should be concerned about this problem. I've searched the forums, and I don't see this problem mentioned, and I do see some output from others showing the correct processor listed (which worries me). Windows DID in fact recognize the correct one... otherwise I would have been concerned about a bait-and-switch scenario.

Any ideas? Here is the output:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           [COLOR="Red"]T2600[/COLOR]  @ 2.16GHz
stepping        : 8
cpu MHz         : 2167.000
cache size      : [COLOR="Red"]2048 KB[/COLOR]
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 4327.17
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           [COLOR="Red"]T2600[/COLOR]  @ 2.16GHz
stepping        : 8
cpu MHz         : 2167.000
cache size      : [COLOR="Red"]2048 KB[/COLOR]
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 4322.84
clflush size    : 64

---

### Post by ola on 2007-05-19
Hi,

I'm not sure about this but what happens if you check the CPU-information while you are doing something that requires a lot of CPU (while starting OpenOffice or something)? It might just be a presentation error?

---

### Post by CSISagent on 2007-05-20
This doesn't make a difference to the shown processor. What it will do is change the frequency shown, due to frequency scaling. Actually, that's how I generated the capture above.

---

