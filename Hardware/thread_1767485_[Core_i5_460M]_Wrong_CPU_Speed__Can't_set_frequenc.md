---
title: "[Core i5 460M] Wrong CPU Speed / Can't set frequency past 1.73GHz"
date: 2011-05-25
forum: Hardware
---

### Post by GTMoraes on 2011-05-25
It's just like the title. The maximum frequency I can get (Using Ubuntu 11.04 Natty Narwhal, installed on a External Hard Drive, on a EXT4 partition and using a PAE Kernel. Latest kernel available thru normal updates) is 1.73GHz from 2.6GHz

This doesn't seems to happen on Windows (which is installed on the main HDD), reporting 2.63GHz on the "Computer Properties", so I kinda discard a BIOS/ACPI Issue.

I've tried everything. Manually setting up the speed higher than 1.73GHz, setting into Performance and everything. I don't want to disable the CPU Scaling, since the machine in question is a laptop (My father's).

I've tried googling around, but I didn't get any good results.

So, what should I do?

P.S.: Just in case you ask, I'm, right now, compiling a Kernel using CONCURRENCY_LEVEL=5 and "make -j5" to use all "4" available "cores". 100% CPU usage right now. Still stuck at 1.73GHz, no matter what I do

P.P.S.: This might be interesting:
```
etmoraes@ETMORAES-SIM:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
stepping	: 5
cpu MHz		: 1733.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
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
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5056.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
stepping	: 5
cpu MHz		: 1733.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5053.86
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
stepping	: 5
cpu MHz		: 1733.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5051.82
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
stepping	: 5
cpu MHz		: 1733.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5055.23
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

etmoraes@ETMORAES-SIM:~$ 

```
I can set through those frequencies: 1.2GHz, 1.33GHz, 1.47GHz, 1.60GHz, 1.73GHz
I can see those frequencies: 1.2GHz, 1.33GHz, 1.47GHz, 1.60GHz, 1.73GHz, 1.87GHz, 2.00GHz, 2.13GHz, 2.27GHz, 2.40GHz, 2.53GHz, 2.53GHz (Yes, twice 2.53GHz)
I kinda feel like there are too many frequencies available, and it gets crazy.

[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by GTMoraes on 2011-05-25
Lil' bump and newsflash

I've ran CPUZ On Windows and stressing the CPU, I've managed to get 2.7GHz (might be the Turbo Boost thing). Also, I've seen the CPU scaling through many frequencies (1.33GHz, 1.47GHz, 1.60GHz, 1.73GHz, 1.87GHz, 2.00GHz, 2.13GHz, 2.27GHz, 2.40GHz, 2.53GHz, 2.7GHz, but not the 1.2GHz. If that means something)

I'll be waiting for updates..
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by elliotbeken on 2011-05-25
If you righ click on the panel and add CPU frequency what does this show ??

---

### Post by GTMoraes on 2011-05-25
Which panel? I'm using the Awn CPU Frequency Applet (works on my AMD box, though)

If I try to set any frequency above the 1.73GHz, it seems like to interpret like if I chosen 1.73GHz..
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by novinick on 2011-05-25
can you send following: 
```
 cpufreq-info
```and also 

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq 

```> $ls /sys/devices/system/cpu/cpu0/cpufreq/
affected_cpus                  scaling_available_governors
bios_limit                     scaling_cur_freq
cpuinfo_max_freq               scaling_driver
cpuinfo_min_freq               scaling_governor
cpuinfo_transition_latency     scaling_max_freq
related_cpus                   scaling_min_freq
scaling_available_frequencies  scaling_setspeed

[https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling](https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling)
[http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html](http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html)

however this looks like a kernel problem about i5 cpu ? or bios-acpi related ?

what is your current  motherboard ?
you have two in signature


i've also learned neat command , thnx 

```
watch grep \"cpu MHz\" /proc/cpuinfo
```

---

### Post by GTMoraes on 2011-05-25
Well, this is embarrassing..

When you told me to run  cpufreq-info, it told me I needed to install the cpufrequtils. Installing this makes the CPU work on any frequency I set.

Weird, but it worked...
Thanks!

------
Whoops, I resign it.

When running on Battery power, the frequency is limited to 1.73GHz. Plugged in, it can go as much as I wish
It sounds logical, but as long as I have the control over the frequency manually, so I want this disabled, thanks =P

[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by novinick on 2011-05-25
here you go

(last troubleshooting item from arch/linux wiki)

> Some cpu/bios configurations may have difficulties to scale to the  maximum frequencies or scale to highter frequencies at all. Sadly there  is only a workaround right now. Add "processor.ignore_ppc=1" to your  kernel boot line and/or edit the value in  /sys/module/processor/parameters/ignore_ppc from 0 to 1. try on the fly,probably need sudo
[COLOR=Red]
**warning , this may overheat ur lap! , if not allready overheated as is**[/COLOR]
```
echo "1" >   /sys/module/processor/parameters/ignore_ppc
```if not working, add it to **grub**
```
processor.ignore_ppc=1
```then reboot and see if you got back missing...frequencies ? lol

:lolflag:

---

### Post by GTMoraes on 2011-05-25
> **novinick said:**
> here you go

(last troubleshooting item from arch/linux wiki)


try on the fly,probably need sudo

```
echo "1" >   /sys/module/processor/parameters/ignore_ppc
```
if not working, add it to **grub**
```
processor.ignore_ppc=1
```then reboot and see if you got back missing...frequencies ? lol

:lolflag:

Many thanks for your effort, but that's not exactly what I want =)

I've discovered that, plugged in, I can select any frequency. Battery powered, it limits to 1.73GHz

Sounds fair but... nah.
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by novinick on 2011-05-25
and is this meaning that is working for you or non working :confused:

what if it melt laptop down on maximum frequency ? :D

> **GTMoraes said:**
> Well, this is embarrassing..

When you told me to run  cpufreq-info, it told me I needed to install the cpufrequtils. Installing this makes the CPU work on any frequency I set.

Weird, but it worked...
Thanks!

------
Whoops, I resign it.

When running on Battery power, the frequency is limited to 1.73GHz. Plugged in, it can go as much as I wish
It sounds logical, but as long as I have the control over the frequency manually, so I want this disabled, thanks =P

[LEFT]__[/LEFT]


---

### Post by GTMoraes on 2011-05-25
> **novinick said:**
> and is this meaning that is working for you or non working :confused:

what if it melt laptop down on maximum frequency ? :D
lol, do you believe I actually thought about this? Compiling the kernel using all cores @ 1.73GHz brought the battery to its knees in less than 30 minutes. 2.53GHz I would't even blink before the battery goes out

But why I can run at max speed on Windows, even powered by battery?

--
Whoops, I wasn't clear: Works plugged in, doesn't work (as I wanted it to work) on battery
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by novinick on 2011-05-25
> **GTMoraes said:**
> Many thanks for your effort, but that's not exactly what I want =)

I've discovered that, plugged in, I can select any frequency. Battery powered, it limits to 1.73GHz

Sounds fair but... nah.
[LEFT]__________________________
[/LEFT]


here thay say it is other way around at least for some thinkpads

[http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling](http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling)

when pluged they get locked down :(
interesting ,huh
:popcorn:

---

### Post by GTMoraes on 2011-05-25
> **novinick said:**
> here thay say it is other way around at least for some thinkpads

[http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling](http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling)

when pluged they get locked down :(
interesting ,huh
:popcorn:

Interesting, indeed..
Sounds pretty damn fair. I don't want to stress out this hardware (it's kinda cheap), better not mess around with it.

Many thanks for your support! Kudos for you =)
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

