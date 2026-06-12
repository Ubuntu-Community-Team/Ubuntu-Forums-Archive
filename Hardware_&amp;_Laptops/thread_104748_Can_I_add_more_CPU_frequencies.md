---
title: "Can I add more CPU frequencies"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by Sutekh on 2005-12-16
CPU scaling seems to be working using the following frequencies;
```
user@ubuntu:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2000000 1800000 1000000
user@ubuntu:~$

```

But I want more options, is this possible?  Here's my cpu info, I noticed that it says stepping: 2, does this mean I can't add more frequency steps? 

```

user@ubuntu:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
**stepping        : 2**
cpu MHz         : 2010.457
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 1990.65

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
**stepping        : 2**
cpu MHz         : 2010.457
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 1990.65
user@ubuntu:~$

```

I also noticed that when I change the frequency using the scaling applet, the value of cpu MHz doesn't change but the bogomips does.  What is the bogomips?  It always seems about twice the amount of the cpu frequency.

Freq Scaling 1.0GHz bogomips 1990.65
Freq Scaling 1.8GHz bogomips 3583.18
Freq Scaling 2.0GHz bogomips 3981.31

Anyway, can I add more frequency steps?  Cheers!

---

### Post by psusi on 2005-12-16
No, you can't.  The hardware only supports those 3.

---

### Post by Sutekh on 2005-12-16
Bummer and Thanks!

---

### Post by Game_Ender on 2005-12-24
That can't be completely true, because I dual boot on my laptop (Inspiron 600M) and in windows the CPU drops to around 150Mhz and here the lowest it will go is 600Mhz on Ubuntu .  Although in my case it gives the following frequencies.
```
1600000 1600000 1600000 1400000 1200000 1000000 800000 600000
```

Which means it has the proper number of levels but doesn't acutally realize what they are.  Is there way I can manually change them?

---

### Post by WildTangent on 2005-12-24
[QUOTE=Game_Ender]That can't be completely true, because I dual boot on my laptop (Inspiron 600M) and in windows the CPU drops to around 150Mhz and here the lowest it will go is 600Mhz on Ubuntu .  Although in my case it gives the following frequencies.
```
1600000 1600000 1600000 1400000 1200000 1000000 800000 600000
```

Which means it has the proper number of levels but doesn't acutally realize what they are.  Is there way I can manually change them?[/QUOTE]
EDIT: Nevermind, I didn't read your whole post.

-Wild

---

