---
title: "Underclocking laptop while on battery power"
date: 2011-05-09
forum: Hardware
---

### Post by memilanuk on 2011-05-09
Hello,

I've got 11.04 running fairly smoothly on my HP Pavillion DV4 laptop.  One thing I'd like to do is see if its possible some way to extend the battery life a bit by underclocking things when on the battery.

In Windows Vista 64-bit, when I clicked on the power settings icon in the toolbar I could select 'high performance' or 'battery saver' as two of the options.  Via some gadgets I have running in the Windows sidebar, I see that in the former mode, the cpu is running @ 2GHz, and in the latter, only 1.2 GHz.  The machine is a bit of a dog on the lower setting, but the battery life difference is noticeably.

Is there a relatively easy and simple way to achieve the same effect in Ubuntu?

Thanks,

Monte

---

### Post by tgalati4 on 2011-05-10
What is the output of:

cat /proc/cpuinfo

If you have a centrino or later Intel processor, then you might be able to use speedstep.  You can change the policy from performance to on-demand and it will adjust the clock speed and save power in the lower speed modes.

It's automatically detected, so other than installing the cpu frequency applet or checking your BIOS power management settings, there's probably not much you can do.  If you know the magic settings to undervolt your processor, that might yield some power settings, at the risk of lower stability.

---

### Post by memilanuk on 2011-05-10
Okay... looks like from the output below that its already automatically throttling back to 1200MHz like you mentioned.

Output of cat /proc/cpuinfo:

```

monte@hp-dv4:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
stepping	: 10
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips	: 3989.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
stepping	: 10
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips	: 3989.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

monte@hp-dv4:~$ 


```

---

### Post by tgalati4 on 2011-05-21
You can undervolt, but you will have to recompile your kernel--and it's a bit of a chore.  You can search for some tutorials.  Basically you want to enable P-Stage Voltage Control.

Here's a link to get you started:  [http://linux.aldeby.org/linux-phc-cpu-undervolting.html](http://linux.aldeby.org/linux-phc-cpu-undervolting.html)

I did it on my Thinkpad T43P running Jaunty and I'm seeing 5C cooler temps.  I've just started tweaking, so I don't know how low I can go.  I'm running a 2.14 GHz Pentium-M (single core) processor.  It throttles from 800 MHz to 2.14 GHz in 6 steps.

In gnome you can add cpufreq panel applet that displays your current running speed and you can select a specific speed or a performance policy.  You can select an undervolt at each speed using another panel tool PHCTool.  Most of your savings will come from the higher speeds, but you don't often run at full bore when on battery.  I'm getting 20 minutes extra time on an older (2-hour) battery.  But I've just started my tweakage.

---

