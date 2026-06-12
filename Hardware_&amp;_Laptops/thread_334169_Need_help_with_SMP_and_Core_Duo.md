---
title: "Need help with SMP and Core Duo"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by honeydew on 2007-01-08
I have recently installed Edgy onto a Sony Vaio VGN-SZ330P.  I have been reading around attempting to get the dual processing working, I am wondering if there is a flag I have to turn on some where currently I am running at half speed(I believe).   I have also read that edgy comes with support for SMP out of the box, so I shouldnt have to install the linux-686/-smp kernel.  Any 
ideas?

here is my output from cat /proc/cpuinfo
```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4006.85

```

I have some experience with Dual processor in BSD enviorments, and I am aware that when running the command top, I should see both processors, however I only see one.  And with the ubuntu graphical system monitor only one CPU is visible.  I cant wait to run with both processors so if anyone has any ideas hook it up! 

everyone have a wonderful day =]

---

### Post by tturrisi on 2007-01-08
Only the smp kernels support dual processors, thus you will need a 686-smp kernel.

---

### Post by honeydew on 2007-01-08
do I have to modify my grub/menu.1st ?

---

### Post by Choxo on 2007-01-08
You will have to install linux-generic kernel I think.

It will be installed, but it won't boot by default the generic.

To do that, you have to gange /boot/grub/menu.lst ...

---

### Post by ~LoKe on 2007-01-08
Just comment the entries for the 386 kernel, assuming you've got the generic one installed.

---

### Post by honeydew on 2007-01-08
okok Im booted in.. I have great success =] with dual processors.. though now it seems that the nvidia driver I had installed is not liking the new kernel. =[  I tried to uninstall and reinstall with synaptic.   but here is the new cat /proc/cpuinfo for enjoyment!

$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4007.34

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4000.56

---

### Post by ~LoKe on 2007-01-08
Yeah, that's one unfortunate thing; you have to reinstall the driver when you use a different kernel.

---

### Post by honeydew on 2007-01-08
well.. a simple reinstall of the driver with synaptic was not working.  Instead I compiled the newest driver from source.. with success!  o and beryl is o sooo sexy.

---

