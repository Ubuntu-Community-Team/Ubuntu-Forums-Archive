---
title: "Dual Core Problems Acer Aspire 5672WLMi"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by Arbiter on 2006-12-07
I've got my laptop now dual booting with Windows XP Pro and Ubuntu Linux (I'd go completely Linux if not for having to do schoolwork in Windows and if Ubuntu supported the built-in webcam and memory card reader).

Anyway, I'm trying to get Edgy to fully utilize the dual core Intel processor I've got in this thing.  I installed the i686-smp kernel and I'm confused by the output of cat /proc/cpuinfo.

<code>

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3333.62

</code>


It identifies my CPU as an Intel dual core chip, but only tells me it only has one core, even after I've installed the i686-smp kernel.

Here is the output of uname -a

<code>

Linux proteus 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

</code>

I'm not sure what exactly to do, any help would be greatly appreciated :)

---

### Post by malbery on 2006-12-26
Arbiter, I have a 5673WLMi and the same kernel as you. Did you get it resolved?
My /etc/cpuinfo lists two processors:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3671.32

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1833.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3667.07

```

---

### Post by malbery on 2006-12-26
Have you tried:

[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg48060.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg48060.html)

---

### Post by cbudden on 2006-12-26
You don't need the -smp kernel, just the linux-image-generic one.  It has built in SMP support.  The webcam also has drivers, follow instructions on the big *** 5672 thread here - [http://www.ubuntuforums.org/showpost.php?p=1896109&postcount=682](http://www.ubuntuforums.org/showpost.php?p=1896109&postcount=682)

---

### Post by fredj on 2006-12-26
The default kernel in Edgy detects and uses both cpus. You don't need to install an
SMP kernel.

---

