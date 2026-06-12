---
title: "[SOLVED] Inspiron 6400 Core 2 Duo"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by blackvd on 2008-01-30
This is weird and I didn't even know it was a problem until I accidentally came across it. I have a Dell Inspiron 6400 Core 2 Duo. When I run

> cat /proc/cpuinfo

I get 

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3728.07
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
stepping        : 12
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3724.05
clflush size    : 64


Since I have a dual core it should say 1 right? So in the thread I found it said to install linux-686-smb and reboot and everything should be most excellent. However, I was unable to find said package. Then I found out I needed linux-generic instead. So I installed that, rebooted and ....nothing? Same thing came up 0? I'm lost here. Any help would be greatly appreciated. Thanks!

---

### Post by eggdeng on 2008-01-30
There hasn't been a separate smb kernel since 6.06. The generic kernel should recognise both cores. You can use the system monitor applet to see if they are being recognised. Right-click on the panel, choose Add to Panel , choose System Monitor in the System & Hardware section and click Add.

---

### Post by blackvd on 2008-01-30
Ok according to system monitor it sees two. But why does cat /proc/cpuinfo show 0?

---

### Post by eggdeng on 2008-01-31
> But why does cat /proc/cpuinfo show 0? You have 2 processors listed. Numbering starts at 0, ergo processor 0 and processor 1.

---

### Post by Yellow Pasque on 2008-01-31
As noted, the cpuinfo shows processor #0 and #1.  Also, in case you're wondering, your processor uses Speedstep/EIST at idle, which reduces the speed to 800MHz (6 * 133MHz system clock).

---

### Post by blackvd on 2008-01-31
Oh Ok, Not sure why I didn't catch that? Thanks for information.

---

