---
title: "Toshiba Tecra A3"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by uccio on 2005-08-08
hi guys, i've installed  my ubuntu and during a postinstall checkup I saw thatmy centrino isn't recognized.

cat /proc/cpuinfo is..:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 798.055
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1576.96


cpu MHz         : 798.055  [-X 
bogomips        : 1576.96  [-X 

My Cebtrino is a 1600Mhz and the bogomips are 3k almost.
This is the right value that i've got with other linux distros (FC4, Mandriva, Knoppix).

I had tried to recompile the kernel 2.6.10 but all isqorking except this. inside the kernel i had choice the Pentium-M support.

Sorry for bad english, I hope someone can help me.

bye
marco Bertolotti  ](*,)

---

### Post by varunus on 2005-08-08
It seems that you are being recognized as a centrino.  What Ubuntu does is include software called powernowd.  This software scales down your processor MHz when CPU activity is low (constant power usage reduction).  On a laptop. you probably want max power when plugged in.  To accomplish this, you can change to a different CPU scaling software called cpufreqd.

```
sudo apt-get install cpufreqd
``` 

This will ask to uninstall powernowd and ubuntu-desktop; go ahead, it won't break anything.

After this, you will notice that scaling works, and that your MHz reads properly when plugged in.  Or at least, you should.  If you don't, can you post the output of lsmod here?  You may need to execute "sudo modprobe speedstep_centrino" in a terminal.

---

