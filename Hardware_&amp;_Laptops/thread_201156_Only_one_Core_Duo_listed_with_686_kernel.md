---
title: "Only one Core Duo listed with 686 kernel"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by mainekid on 2006-06-21
Hi,
I have an MST Speedster 945GT motherboard fitted with a Core Duo T2500 CPU.  I had orginally installed Ubuntu Desktop 6.0.6 and after install the 686 kernel, it was able to see both CPU's.  Now, I have installed Ubuntu server and an areca RAID card (1210). Now cpuinfo only reports 1 CPU core.  I tried installng the stock linux-686 kernel instead of the server version, but that didn't help.  Can someone suggest somethng else to try?

Thanks!

More information
uname -a
Linux ldc 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

more /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1992.127
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 x
tpr

---

