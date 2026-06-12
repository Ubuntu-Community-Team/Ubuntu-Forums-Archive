---
title: "Dual CPU Issues"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by lykoszine on 2007-04-30
Guys,

I have a dual CPUs (PIII Coppermine) that don't seem to be working in a beta of Feisty upgraded to the latest as of a couple of days ago.

uname -a
Linux desktop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 648.272
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1297.48
clflush size    : 32

only seems to identiy one processor. Is this a bug?

I remember installing smp kernels some time ago, but now with the fiesty install I have a generic kernel (with restricted nvidia modules).

Is this a bug? Can someone lend a hand?
S

S

---

### Post by veloce on 2007-04-30
> **lykoszine said:**
> Guys,

I have a dual CPUs (PIII Coppermine) that don't seem to be working in a beta of Feisty upgraded to the latest as of a couple of days ago.

uname -a
Linux desktop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux



I get: 

uname -a
Linux CAALT18 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

Note the SMP returned for me.  Somehow you haven't ended up with the SMP kernel.  No idea how to fix it though.

---

### Post by lancest on 2007-04-30
Only 1 CPU running on Feisty!!! Laptop dual core. Fresh install yesterday
Why????
  cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 996.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.62
clflush size    : 64

---

### Post by lancest on 2007-04-30
WTF?
Linux CalLinux-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux
No SMP?

---

### Post by veloce on 2007-04-30
> **lancest said:**
> WTF?
Linux CalLinux-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux
No SMP?

2.6.20-15-**386**

That seems to be the other similarity.  Mine has used the "-generic" kernel.

But, still, no idea how to fix it, sorry.

---

### Post by lykoszine on 2007-05-02
Guys,

As someone pointed out in a separate thread, all that is happening is the 386 kernel appearing higher in the grub menu than the generic kernel, so so the 386 is getting loaded...

Just update /boot/grub/menu.lst and comment out or move the 386 kernels, and 
sudo update-grub
to fix.

doh.

S

---

### Post by lancest on 2007-05-02
Yes I just added the generic kernel and no problem both CPU show. Grub very easy to adjust. Thanks. Nice command  Got Nvidia working after researching these forums. Linux is a great chance to learn.

---

