---
title: "Ubuntu 7.04 and pentium m 1.6"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by jaideep_jdof on 2007-07-13
I am using ubuntu 7.04 on my compaq presario v2000 laptop with pentium m 1.6 processor, this is the output of my uname -a:
```
Linux jaideep-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
```

The problem i am facing is that the cpu freq steps are wrong, it should vary between 600mhz and 1.6ghz but in ubuntu 7.04 its varying between 798mhz and 1596 mhz.

How can i correct this.
Is it a bug.

---

### Post by snap on 2007-07-13
Strange, i've got a Pentium M 1.8Ghz, seems fine here, 600 to 1800,

try 

```
sudo cat /proc/cpuinfo
```

it should show the exact current ghz the cpu is running at.

I am not at my ubuntu box now so i'll check it out later to see if it could be an issue with the gnome cpufreq-applet

---

### Post by jaideep_jdof on 2007-07-14
Same problem is there in kubuntu 7.04, so its not a problem with gnome cpufreq-applet, following is the output of sudo cat /proc/cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 798.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 1198.22
clflush size    : 64
 
```

---

### Post by Djembe on 2007-07-14
> **jaideep_jdof said:**
> I am using ubuntu 7.04 on my compaq presario v2000 laptop with pentium m 1.6 processor, this is the output of my uname -a:
```
Linux jaideep-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
```

The problem i am facing is that the cpu freq steps are wrong, it should vary between 600mhz and 1.6ghz but in ubuntu 7.04 its varying between 798mhz and 1596 mhz.

How can i correct this.
Is it a bug.

It's not a bug.  it's just the way it reads your CPU.  my CPU, a P-M 1.86 Ghz, is reported to go from 798 Mhz to 1862 Mhz, and while the actual variance is between 800 Mhz to 1866 and 2/3 Mhz, Ubuntu doesn't read the fractions in the CPU multiplier.  The actual multiplier for my CPU is 133 and 1/3 Mhz, but Ubuntu isn't reading the extra 1/3, so it reads the CPU speed as slightly lower than it actually is.  There's nothing wrong.

---

### Post by jaideep_jdof on 2007-07-15
But even if it reads like this, it should vary between 600mhz  and 1.6 ghz, not between 800 mhz and 1.6 mhz.

---

