---
title: "Pentium M CPU running too slow"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by linuxpyro on 2007-11-20
I have a Toshiba Tecra M2 Laptop with a 1400 MHz Pentium M processor running Gutsy.  My problem is that my CPU only runs at 600 MHz, as shown in the output of cat /proc/cpuinfo:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 600.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2
bogomips        : 1198.26
clflush size    : 64
 
```

I have been messing with frequency scaling in trying to fix this, and went through the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=248867&highlight=toshiba+laptop+cpu+kernel").  I tried setting the cpu governor to performance, but this did not change anything.  I tried setting it to userspace, and then tried to change the frequency by doing cpufreq-selector -f 1500000.  While that command did not return any errors, it also did not increase my cpu frequency.

I started poking around in /sys/devices/system/cpu/cpu0/cpufreq, and found the following that seems interesting.

In cpuinfo_max_freq:
```

600000

```

In cpuinfo_min_freq:
```

75000

```

In scaling_available_frequencies:
```

75000 150000 225000 300000 375000 450000 525000 600000

```

In scaling_max_freq:
```

600000

```

And in scaling_min_freq:
```

600000

```

I'm not really sure what to make of this.  I've been searching the forums, but thus far have not found anything helpful (sorry if I missed something...).  Anyone have any ideas?

---

### Post by angryfirelord on 2007-11-20
Are you sure it's not just idle? Open up two terminals, run **glxgears** in one and then run **cat /proc/cpuinfo** in the other.

---

### Post by linuxpyro on 2007-11-20
Still the same thing, the CPU's only running at 600 MHz.

---

### Post by angryfirelord on 2007-11-20
After looking at your post, I'm noticing that your cpuinfo_max_cpu is reading 600000, which would be 600MHZ. I'm using powernowd on a Core 2 Duo with no issues. 

My suggestion is to remove whatever you installed for power management, put powernowd back, and install emifreq-applet. You can add it to your gnome panel (it'll be the last entry) and you can adjust the frequency that way.

If that doesn't work, then I'll have to think of something else.

---

