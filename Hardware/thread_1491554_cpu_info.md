---
title: "cpu info?"
date: 2010-05-23
forum: Hardware
---

### Post by yim on 2010-05-23
I have an AMD Phenom II X4 965 3.4 it is detected as  

ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 965 Processor
stepping	: 3
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6830.24
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


frequency @ 800 mhz 

scratching my head on that one mint9 same thing of corse

any ideas

---

### Post by 2hot6ft2 on 2010-05-23
In 10.04 it's in ondemand by default so when it's not under a load it's at the lowest setting. Right click on the top panel and select Add to Panel then select CPU Frequency Scaling Monitor and click Add then Close.
Now left click on the new applet and set it to Performance and check again.
I'm pretty sure that's what it is. You can always right click on the applet and select Remove from Panel to get rid of it.
And oooh a AMD Phenom II X4 965, I am soooo jealous right now...;)
:guitar:

---

### Post by yim on 2010-05-23
I appreciate the info and you were right on the spot , as far as being jealous, if it makes you feel better, I saved for over a year to replace motherboard and cpu and memory, lol, I had no idea how far ahead this thing would be from a ht P4 3.0. Never really thought that thing ran like it should but maybe I expected too much. anyhow I really appreciate your help

thanks yim

---

### Post by yim on 2010-05-23
I appreciate the info and you were right on the spot , as far as being jealous, if it makes you feel better, I saved for over a year to replace motherboard and cpu and memory, lol, I had no idea how far ahead this thing would be from a ht P4 3.0. Never really thought that thing ran like it should but maybe I expected too much. anyhow I really appreciate your help

thanks yim

---

### Post by 2hot6ft2 on 2010-05-23
You're welcome. I've been considering building a box myself so when I saw the Phenom quad core I know that has to be sweet. Enjoy it, I know I would.
:guitar:

---

### Post by cascade9 on 2010-05-24
> **yim said:**
> I appreciate the info and you were right on the spot , as far as being jealous, if it makes you feel better, I saved for over a year to replace motherboard and cpu and memory, lol, I had no idea how far ahead this thing would be from a ht P4 3.0. Never really thought that thing ran like it should but maybe I expected too much. 

A X4 965 should be so much faster than a P4 3.0 HT that its not funny. Even if it was running slightly 'crippled' (eg DDR2 667, no the 800/1066 it would like, using an IDE drive, not SATA, etc) it should still be a lot faster.

---

