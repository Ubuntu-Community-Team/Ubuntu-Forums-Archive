---
title: "Multithreaded CPU detection?"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by oxygen_77 on 2006-01-23
Hey, I have a Fujitsu Lifebook N6010 with a Pentium 4 processor.  When running this machine under windows XP the CPU was displayed as two CPU's much like a dual core Athalon would do.  Now that I'm running Breazy when I type
```
sudo cat /proc/cpuinfo
```
I get the following
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 1
cpu MHz         : 1868.089
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6340.60

```
Is there a way to get this to recognize the CPU as two CPU's?  Thanks!

---

### Post by Sutekh on 2006-01-24
Do you have a SMP (Symmetric Multi-Processing) kernel installed?

The command
```
uname -r
```
will tell you the kernel you are running.

---

### Post by oxygen_77 on 2006-01-24
hmmm...  maybe not because when I typed the code above I get:

2.6.12-10-386

So does that mean I should recompile the kernel?  Which versions are multiprocessor aware?

Thanks.

---

### Post by frodon on 2006-01-24
to enable hypperthreading you need to install the smp kernel, you will really improve the performances doing that : [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by Sutekh on 2006-01-24
And because you are using the P4 processor you want to install the 686-SMP kernel (there are no 386-SMP kernels)
```

sudo apt-get install linux-686-smp

```

---

### Post by oxygen_77 on 2006-01-24
thanks for the help everyone.  I'll give it a try tonight.

---

### Post by oxygen_77 on 2006-01-24
thanks for the help everyone.  I'll give it a try tonight.

---

