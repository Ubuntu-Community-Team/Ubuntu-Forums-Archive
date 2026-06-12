---
title: "No sound in new install UB 16.04"
date: 2017-11-21
forum: Hardware
---

### Post by rapattack on 2017-11-21
I did a new install on this machine last night and have alway found it hard to get the sound happening in Linux. I have a speaker system plugged into the onboard sound and doesn't seem to matter what i select in sound settings/volume control i am getting nowhere. Seems a lot is greyed out like the speaker icon in the tray next to the date and sometimes when i am adjusting settings the speaker icon goes red therefore i guess showing me it is mute? I am sure the speaker system is on and plugged in. I always know as there is a sound it makes through the speakers. I think last time i did a fresh install on another machine a couple of years ago someone sent me a tutorial maybe but googling has not brought anbything reflecting this version of linux or anything close to it. I do understand ubuntustudio has all sorts of fancy sound things that i have found it impossible to master. I stick to stuff i can work with like audacity and cinelerra that doesnt rely on that

---

### Post by Autodave on 2017-11-22
Type and specs on your machine? Do you know what sound card it has?

---

### Post by rapattack on 2017-11-23
Oh thanks i found out the issue. Silly me i didnt see that there is a 'tick' i was supposed to uncheck in the 'sound settings' icon in the tray. I never have seen that before gee. This is a version of UB i havent used before. I dont know the specs i am afraid as i cant get into the bios for some reason but i did learn this command today:
sudo cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
stepping	: 5
microcode	: 0x2
cpu MHz		: 3592.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida arat
bugs		:
bogomips	: 7200.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
stepping	: 5
microcode	: 0x2
cpu MHz		: 1197.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida arat
bugs		:
bogomips	: 7200.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
stepping	: 5
microcode	: 0x2
cpu MHz		: 1463.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida arat
bugs		:
bogomips	: 7200.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
stepping	: 5
microcode	: 0x2
cpu MHz		: 1463.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida arat
bugs		:
bogomips	: 7200.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by rapattack on 2017-11-25
Good news its working. I didnt realise there was a 'mute' thing checked in the sound settings. Well this has been the easiest install to fix once i opened my eyes lol

---

