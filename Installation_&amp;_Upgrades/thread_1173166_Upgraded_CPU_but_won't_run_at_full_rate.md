---
title: "Upgraded CPU but won't run at full rate"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by barnabear on 2009-05-29
Hi, I just upgraded the CPU on my 64 bit 8.04 (Hardy) PC from an intel E1200 to an Intel E5200. This should run at 2.5 GHz.

The frequency monitor is flipping between 1.2 and 1.7 GHz, depending on load, and is indicating 1.7 GHz as the maximum.

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq gives

1700000

the same value for scaling_max_freq too. Neither of these files seem to be writeable to any effect.

How can I get the full 2.5 GHz out of this processor? The BOGOMIPS count is 5000 per core, which is correct.

Thanks in advance.

cat /proc/cpuinfo gives ... 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping        : 10
cpu MHz         : 1200.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov                                              pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant                                             _tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr l                                             ahf_lm
bogomips        : 5003.85
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping        : 10
cpu MHz         : 1200.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov                                              pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant                                             _tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr l                                             ahf_lm
bogomips        : 4999.97
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by iponeverything on 2009-05-29
I don't think that its an OS issue. Perhaps you need change the settings in your BIOS.

---

### Post by barnabear on 2009-05-29
Turns out you are right. The box is my MythTV plugged into our LCD TV as a PC monitor, but the TV won't do the BIOS setup screen resolution, so I took a shortcut and just assumed it would work.

Plugging a real monitor in, I went into the BIOS screen "Motherboard Intelligent Tweaker". This showed the old settings for the E1200. I clicked on "Load Optimised Defaults", which gave me a hint. Rebooted without saving, entered BIOS setup again and set the values I wanted manually. Now it works.

Thanks.

---

### Post by wpshooter on 2009-05-29
Hmmmmmmmm.

You would have thought that upon first boot after changing the processor, that you would have been prompted by the BIOS regarding the change and would have been given a chance to go into setup and adjust the processor speed.  Are you sure that you weren't prompted in this regard ?

---

### Post by barnabear on 2009-05-29
It might have shown me a prompt, but I wouldn't have seen it. I see the initial text screen giving memory test count and the level of the BIOS, but then the screen blanks and I get nothing until the Ubuntu logo and the oscillating progress bar (and sometimes the routine fsck).

It's working now, which is the main thing. Lesson learned - don't be so lazy and connect up a monitor to check the BIOS.

Thanks.

---

