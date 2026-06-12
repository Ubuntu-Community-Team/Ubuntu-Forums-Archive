---
title: "Not All Processors are Seen in System Monitor - Ubuntu 11.04 - Sony Vaio i7 - VPCF1"
date: 2011-08-09
forum: Hardware
---

### Post by jmort253 on 2011-08-09
I installed Ubuntu 11.04 64 Bit 4 weeks ago and in System Monitor it shows all 8 processors. 

Today, VMWare refused to load a VMImage that used 2 processors, and this is what made me aware of the problem with the missing processors.

Today I look in System Monitor and there is only 1 processor. I also ran cat /proc/cpuinfo and you can see there is only 1 processor. 

I tried booting on kernel 2.6.38.8 and 2.6.38.10 and both show the problem.

How do I get the other 7 back?


```

jem@jem-VPCF136FM:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 30
model name	: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
stepping	: 5
cpu MHz		: 933.000
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3458.17
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

UPDATE:  I removed "**nolapic**" from the default boot entry in grub. I also changed "**gfxpayload=$linux_gfx_mode**" to "**gfxpayload=text**".  The processors reappeared in System Monitor, but now I'm having a problem with the computer completely freezing up while on Skype or GTalk Video calls.


I've included a photo of my default boot entry in grub:

[IMG]https://lh3.googleusercontent.com/-R_UEmTwLcuA/TkIR7dKxaII/AAAAAAAABDM/EYb8ksH4MFA/s800/IMG_20110809_220220.jpg[/IMG]
[https://lh5.googleusercontent.com/-R_UEmTwLcuA/TkIR7dKxaII/AAAAAAAABDM/EYb8ksH4MFA/photo.jpg](https://lh5.googleusercontent.com/-R_UEmTwLcuA/TkIR7dKxaII/AAAAAAAABDM/EYb8ksH4MFA/photo.jpg)


Hope this helps.

---

