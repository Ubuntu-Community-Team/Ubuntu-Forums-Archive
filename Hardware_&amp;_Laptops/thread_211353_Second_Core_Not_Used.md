---
title: "Second Core Not Used?"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by FabreNZ on 2006-07-08
I think my laptop's second core isn't being used in Linux.  It is enabled in the BIOS, and it works in Windows.  In Linux, the system monitor app only shows one CPU meter (although I don't know if this could be both core graphs combined), and native games such as Sauerbraten run noticably slower than the Windows versions do.

This is the output of "vi /proc/cpuinfo":

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 997.693
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor vmx est tm2 xtprbogomips        : 1997.68

I found "proc/acpi/processor", and it only contains CPU0.  I would think it should contain the cores in seperate folders.

I have just started using Linux, so it is quite a learning curve for me.  Any help (preferably using words a Linux newbie can understand) would be appreciated.

---

### Post by rbalfour on 2006-07-08
can you post the kernel version?

$ uname -a

---

### Post by FabreNZ on 2006-07-08
That returns:

Linux matt-laptop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

---

### Post by ctgray on 2006-07-08
you should install the 686-smp kernel

sudo aptitude install linux-686-smp

(I'm on Windows at the moment but it should be similar to that. Try
apt-cache search 686 | grep smp
if the above doesn't work, and it will give the name of the smp kernel).

---

### Post by FabreNZ on 2006-07-08
That worked perfectly, both cores are now showing up in "proc/acpi/processor" and in the system monitor.  Thanks for the help!

---

### Post by rbalfour on 2006-07-08
> **FabreNZ said:**
> That returns:

Linux matt-laptop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

Thought that's what the problem was...ctgray beat me to the punch...
BTW, when you get the SMP kernel installed, you might want to remove the 386 kernel. Takes up space.

---

