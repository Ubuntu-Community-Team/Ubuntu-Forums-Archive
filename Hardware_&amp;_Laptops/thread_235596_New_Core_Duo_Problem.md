---
title: "New Core Duo Problem"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by techgnome on 2006-08-13
I am running Ubuntu 6.06 on a Sony Vaio SZ240 with a Core Duo processor.  I have followed all of the core duo recommendations I can find online for getting the dual processor feature running to no effect. I started with the Live CD install, then ran sudo apt-get update && sudo apt-get install linux-686-smp.  After rebooting, /proc/cpuinfo atill shows only one processor.  Booting this same system into Windows XP shows both processors running, so I know it can work.  Here is a capture of both my uname -a and cat /proc/cpuinfo:

$ uname -a
Linux techgnome 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1667.113
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor est tm2 xtpr
bogomips        : 2003.30



Anyone have any ideas?  Thanks in advance!

---

### Post by ltmon on 2006-08-13
Wish I could help.  I have a core duo T2400 in an Asus notebook (Asus make the Vaios I think), and it worked fine with just the steps you took.

Do you see two cpus in /sys/devices/system/cpu?

Is there any other debug output or settings I have that could help you?

L.

---

### Post by techgnome on 2006-08-14
No, there is only on cpu listed in /sys/devices/system/cpu.  I have  even tried uninstalling and reinstalling the 686 kernel (as well as the 686-smp kernel).  No change.  Thanks anyway.

---

