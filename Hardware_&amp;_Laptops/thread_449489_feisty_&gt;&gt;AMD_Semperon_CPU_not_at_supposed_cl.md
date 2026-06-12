---
title: "feisty &gt;&gt;AMD Semperon CPU not at supposed clockrate?"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by blu3ness on 2007-05-20
Hello guys, recently installed ubuntu 7.04 on my compaq presario laptop, got almost everything working, last night I tried to suspend so the machine went to stand-by mode as usual, but when I wake up and tried to get him back from sleep, the laptop just kinda dies out on me, the harddrive seems to still be running, just that all the external devices like the mouse or the keyboard are not responding anymore.. so I would appreciate it if anyone knows anything related to this.

Additionally... while I was looking ito this problem, it appears that something else that's fishy caught my attention, I have a semperon 3300 at 2.0 Ghz CPU, however, this is what my /cat/cpuinfo gives me

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : Mobile AMD Sempron(tm) Processor 3300+
stepping        : 2
cpu MHz         : 800.000
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 1597.06
clflush size    : 64


```

Is this something that's weird? Ubuntu certainly isn't operating at my max clockrate.

---

### Post by mikewhatever on 2007-05-20
Laptop cpus usually get scaled down to reduce power usage and heat output. That means that when the laptop is idle or nearly so, the cpu would be running at a lower speed. Try loading some programs, even a DVD movie and run that command again. If the speed does not go up, then you need to worry.

---

### Post by blu3ness on 2007-05-20
thank you mikewhatever, apparently I was just worrying too much, yes, the cpu adjusts its clockrate automatically, sweet :P

---

### Post by Guranic on 2007-05-20
Hi! Check this thread [http://ubuntuforums.org/showthread.php?t=304570](http://ubuntuforums.org/showthread.php?t=304570) It gives you nice gui tool for Gnome.

---

