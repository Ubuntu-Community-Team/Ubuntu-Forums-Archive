---
title: "CPU throttling issues, Hardy+Q6600"
date: 2008-07-22
forum: General Help
---

### Post by Nebbuchanezzar on 2008-07-22
so, I am running a Q6600, and i overclocked it [currently at 3.6GHz...]and it seems to be running at that speed [comparing folding@home frame times, it seems about right...] however, i have sensor-applet installed, and it will only say 2.4...and when ubuntu is started, it gives me the no cpu scaling support error...ive been looking around, and have found a few things that seem a little of...for one, ive read many places, if you type ```
sudo /usr/bin/cpufreq-selector -g performance
``` it changes it to the "Performance" power-saving mode, and this exact code worked on another rig of mine, an X2-5000, also running HH 8.04...well, to say the least, this code didnt work on my Q6600, and i think i found why...in the same spot, the person suggested ```
$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
``` to see the available frequencies, and it again, didnt work...i finally tried to cd as far in as i could, and realized there is no cpufreq dir in any of my cpu folders... what i mean, is if in a terminal, i type ```
cd /sys/devices/system/cpu/cpuX
dir
``` X=[0-3]
i get this output```
cache  cpuidle  crash_notes  online  thermal_throttle  topology
``` clearly, lacking the cpufreq folder.

i guess my main question is: how do i get everything to register that my cpu truly is running where i have it clocked at, and 2: if it is needed, where/how would i get the cpufreq folder back into my cpuX folders?

[HERE](http://foldingforum.org/viewtopic.php?f=12&t=2342) is where i got most of the info, and i have tried most the stuff in that thread there...

any help is greatly appreciated, and tyia... ;-)

~Nebbuchanezzar

---

### Post by DagMan on 2008-07-23
I can answer the first part of the question about looking at your current cpu speed, but only in relation to the actual scaling down of the speed, and not the overclocking speed.
do this
cat /proc/cpuinfo

you can see with mine the first time it shows the capability and then that it is running at the full capability, and in the second one it's scaled,so it shows the capability and says
MHz		: 562.500:
```
$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor          900MHz
stepping	: 8
cpu MHz		: 900.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts
bogomips	: 1801.88
clflush size	: 64

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor          900MHz
stepping	: 8
MHz		: 562.500
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts
bogomips	: 1801.88
clflush size	: 64

```

For the second half of the question.  It is almost always where the cpufreq folder shows up, all the time that I've seen in fact, but in the past it's never existed for me until I loaded the kernel module that let me use scaling.  I would guess that either the folder is somewhere else, or the module to scale the cpu is not loaded.

I have read that when you overclock, you don't see the changes applied in either the /proc filesystem where I looked, or in the available frequencies in /sys.  If I remember correctly, the info in the /proc filesystem is pulled off of the cpu, and the cpu can't be expected to update itself to say that it is overclocked, and the info that shows up in the /sys filesystem that you're poking around for is data that is pulled out of the kernel module, which if you looked at it before it was compiled you would see the appropriate scaling frequencies for the processors, so again it's a hardcoded thing as far as reporting the info goes.  It doesn't mean that the cpu isn't overclocked, it just means that the info about the cpu doesn't change in either of those places.


The module to scale that cpu, I think, is acpi-cpufreq but there sure is a lot of bug reports regarding it not handling it.  I had a differant core 2 that used that module and I had to modprobe it twice, the first time it would give an error.
Might try the solution discussed here if you end up with problems. [http://forums.fedoraforum.org/showthread.php?t=131786](http://forums.fedoraforum.org/showthread.php?t=131786)

---

### Post by Krupski on 2008-07-23
> **Nebbuchanezzar said:**
> so, I am running a Q6600, and i overclocked it [currently at 3.6GHz...]and it seems to be running at that speed [comparing folding@home frame times, it seems about right...] however, i have sensor-applet installed, and it will only say 2.4...and when ubuntu is started, it gives me the no cpu scaling support error...ive been looking around, and have found a few things that seem a little of...for one, ive read many places, if you type ```
sudo /usr/bin/cpufreq-selector -g performance
``` it changes it to the "Performance" power-saving mode, and this exact code worked on another rig of mine, an X2-5000, also running HH 8.04...well, to say the least, this code didnt work on my Q6600, and i think i found why...in the same spot, the person suggested ```
$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
``` to see the available frequencies, and it again, didnt work...i finally tried to cd as far in as i could, and realized there is no cpufreq dir in any of my cpu folders... what i mean, is if in a terminal, i type ```
cd /sys/devices/system/cpu/cpuX
dir
``` X=[0-3]
i get this output```
cache  cpuidle  crash_notes  online  thermal_throttle  topology
``` clearly, lacking the cpufreq folder.

i guess my main question is: how do i get everything to register that my cpu truly is running where i have it clocked at, and 2: if it is needed, where/how would i get the cpufreq folder back into my cpuX folders?

[HERE](http://foldingforum.org/viewtopic.php?f=12&t=2342) is where i got most of the info, and i have tried most the stuff in that thread there...

any help is greatly appreciated, and tyia... ;-)

~Nebbuchanezzar

It seems like the 'powernowd' daemon isn't running. And, it SHOULD already be installed in Ubuntu 8.04.1

Try this:

```

/etc/init.d/powernowd restart

```

If it works, you should see:

```

* Stopping powernowd:                [ OK ]
* Starting powernowd...              [ OK ]

```

...and your 'cpufreq' directories should come back.

...although you will have to look at the log files to find out why it's not running in the first place.

---

