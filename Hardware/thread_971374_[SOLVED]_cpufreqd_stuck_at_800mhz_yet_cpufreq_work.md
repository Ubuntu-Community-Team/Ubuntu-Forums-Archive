---
title: "[SOLVED] cpufreqd stuck at 800mhz yet cpufreq working fine."
date: 2008-11-04
forum: Hardware
---

### Post by tehownt on 2008-11-04
So here's the little story/mess:

I have that XPS M1330 running cpufreq successfully in **Ubuntu 8.10 kernel 2.6.27-7-generic** with ondemand, performance, userspace and conservative governors available.

I've also got **cpufreq_acpi** and **speedstep-centrino** modules correctly loaded.

I've been using a simple cpufreq 'ondemand' setup that comes with ubuntu stock without any problems, ( i.e. choses between 800mhz and 2.4ghz depending on load) but I wanted to make it more "intelligent", i.e. switch from a 'performance' running at 2.4ghz when plugged in and when running on battery, keep the original 'ondemand' (800000-2400000) mode.

I thus installed **cpufreqd 2.3.3-1** (from the repos), reading somewhere that it was more efficient than laptop_mode scripts and I thus checked that every section related to CPU control in laptop_mode config files was commented out.

I used a very simple cpufreqd configuration (*/etc/cpufreqd.conf*) as follows, which is used by the daemon ran at startup (init.d):
```

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=5
[/General]

[Profile]
name=Performance High
minfreq=2401000
maxfreq=2401000
policy=performance
[/Profile]

[Profile]
name=Performance Low
minfreq=1600000
maxfreq=1600000
policy=performance
[/Profile]

[Profile]
name=Powersave High
policy=ondemand
maxfreq=2400000
minfreq=800000
[/Profile]

[Profile]
name=Powersave Low
maxfreq=1600000
minfreq=800000
policy=ondemand
[/Profile]

[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]

[Rule]
name=AC Off - Medium Battery
ac=off                   # (on/off)
profile=Powersave High
[/Rule]

[Rule]
name=CPU Too Hot
acpi_temperature=65-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

```

Now for the best part of this:

cpufreqd has absolutely no problem detecting the AC on/off (eventhough it 'craps' the daemon.log with battery status access errors (searching energy_full and energy_now instead of charge_full and charge_now, but this should have been corrected in 2.3.3)) and it even manages to switch between different profiles, but when switching to the 'ondemand' profiles the CPU frequency is **locked at 800mhz**.

i.e. the file */sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq* and scaling_min_freq contain '800000' and cpufreq-info states that both cores are in 'ondemand' governor mode that choses between 800mhz and 800mhz.
```

analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.40 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: ondemand, conservative, powersave, userspace, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

```
All my cpufreq settings seems to be fine, here's the contents of the files located in */sys/devices/system/cpu/cpu*/cpufreq/* :
```

affected_cpus:
0 1
cpuinfo_max_freq:
2401000
cpuinfo_min_freq:
800000
related_cpus:
0 1
scaling_available_frequencies:
2401000 2400000 2000000 1600000 1200000 800000 
scaling_available_governors:
ondemand conservative powersave userspace performance 
scaling_cur_freq:
800000
scaling_driver:
acpi-cpufreq
scaling_governor:
ondemand
scaling_max_freq:
2401000
scaling_min_freq:
800000
scaling_setspeed:
<unsupported>

```
I've spent a lot of time trying to understand what the problem is, I've even tried to add an exec_post parameter in order to modify scaling_max_freq to 2401000 (or 2400000) at the end of the cpufreqd.conf profile, and according to the daemon.log it runs fine (exit 0)
```

exec_post=echo 2401000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

```
or
```

exec_post=cpufreq-set -g ondemand -u 2400000

```


but it doesn't change squat in the file (I've double-checked monitoring file modifications with fileschanged) eventhough it works when I do it manually.

The strange thing is that if I restart the cpufreqd daemon when the laptop is unplugged, sometimes (yes only sometimes) the scaling_max_freq file is correctly set to 2400000, then if I replug the laptop it correctly switches to performance-2400000-2400000, but as soon as I unplug it it falls back into the ondemand-800000-800000 eventhough the config specifies otherwise.

I haven't been able to set ondemand with max to 2400000 and min to either 1200000,1600000 or 2400000 for that matter.

Here's a *cat /proc/cpuinfo* for the record:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
stepping	: 6
cpu MHz		: 2401.000
cache size	: 3072 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips	: 4787.99
clflush size	: 64
power management:

```
and an lsmod | grep -i freq
```

acpi_cpufreq           15500  1 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
processor              42156  4 acpi_cpufreq,thermal

```

I've also tried to switch the */etc/default/cpufreqd* config so as to use centrino-speedstep without success, and raising the verbosity level in cpufreqd doesn't help since there's no obvious 'error' per se and all the Profiles are apparently correctly configured (verified using cpufreqd-get).

So I mean... What the hell ?? Has anyone any idea of what that mess is about ?

Thankfully I can just disable cpufreqd and use the normal ondemand mode but I cannot switch dynamically depending on the power source... 

[CENTER]:confused::confused::confused:[/CENTER]

---

### Post by Lord Xeb on 2008-11-05
You need to go back and install what you had for default. I believe it is powernowd or something.

---

### Post by tehownt on 2008-11-05
Thanks for the suggestion, but I had neither cpufreqd nor powernowd installed by default and chose to get cpufreqd beacause powernowd hasn't been updated for nearly a year and I read that was more tuned for AMD processors.

I'll give it a try but I'm not quite sure it can fullfill my needs. It's a pity cause cpufreqd really was very close to fully working.

---

### Post by Lord Xeb on 2008-11-05
Well actually if you remove that it mucks your frequency up. It does more than just AMD

---

### Post by tehownt on 2008-11-05
Yeah I checked it out and it seems to be also compatible with Intel chips, but it's not very flexible in terms of config and none of the 4 available modes can quite fit my needs compared to cpufreqd, it's not that much developed anymore so I don't think I'll be going that way (honestly, there's no match between the 2).

Btw the default settings in ubuntu is a simple script in init.d setting cpufreq ondemand with -d 0 -u 0 (auto) so no powernowd or other "intelligent" daemon changing frequency on battery/heat/usage status.

I'll keep on searching...

---

### Post by gmc on 2008-11-06
There use to be an entry in /apps/gnome-power-manager (Configuration Editor) that allowed Gnome to set the cpu govenor depending on if the system is running on AC or Battery, however it seems to have been depreciated and is no longer there.

My solution was to create a file in /etc/acpi/battery.d that set the govenor to powersave and a similar file in /etc/acpi/ac.d that sets the govenor to ondemand. (make sure the scripts are executable).

Gord

---

### Post by tehownt on 2008-11-08
Thanks for the info, indeed this is what I tried next thereafter.

I contacted the guy which develops cpufreqd (very sympathetic btw) and we figured out the problem using **strace** and **inotify**.

I updated **cpufrequtils** to the latest **005** version and **cpufreqd** to **2.3.3-3** (instead of -1 in the main repo).

cpufreqd had no problem trying to set the frequency, but for some reason the file *scaling_max_freq* returned to a default 800000 value.

While testing all of this, I noticed that if I was using cpufreqd to set the frequency right after I unplugged the laptop, it wouldn't work for around 10 seconds (It would say that the frequency was correctly set but in fact it wasn't), this I tested using */etc/acpi/battery.d/ and ac.d/*.

In fact, there seems to be **some laptops which require some 'settling' time before changing the frequency/governor**, this could be related to a bug in libcpufreq or the kernel but I wouldn't know.

Anyways, all of this can be corrected thanks to a very nice feature **cpufreqd** supports, which is namely

```

double_check=1

```
 in the [general] section of */etc/cpufreqd.conf*

this will make sure that the settings cpufreqd tries to put in place are correctly set by re-reading the *scaling_max_freq* and *scaling_min_freq* files, cpufreqd will then try to set it as long as it's not correct.

For instance, for me, it takes about 10 seconds for the frequency to be correctly set.

I also noticed using inotifywait that sometimes the *scaling_max_freq* file gets read in a loop by some process which I wasn't able to identify (it wasn't cpufreqd), especially when the laptop was re-plugged on AC (the feature which I had no problem with)... Quite strange.

So I consider this partially [SOLVED] as I found a workaround, I hope this will help someone in the future (it would make it up for the time I lost searching for a solution) ;)

---

### Post by orbisvicis on 2008-11-14
That was incredibly useful. Thank you.

[Edit] But now if you are in the buggy ondemand state and plug the ac-adapter back in, the cpu frequency doesnt change. i.e. it will stay at ondemand minimum-minimum range even though the battery is charging

---

### Post by tehownt on 2008-11-14
That's strange because I have no problem going from ondemand-800000-2400000 to performance-2400000-2400000 back and forth.
Which settings are you trying to set up ? Maybe you could try and launch cpufreqd with verbose 7
```

cpufreqd -D -V7

```
and see what's happenning (maybe it's something else preventing you from changing the value). 
Usually with the double_check parameter, cpufreqd will tell you if he fails changing the values.

---

### Post by orbisvicis on 2008-11-14
My cpu stats (cpufreq-info)
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: powersave, ondemand, performance

I set double_check=1 and start cpufreqd -DV7 while the AC-adapter is pluggin in:
cpufreqd_set_profile     : Policy correctly set 1833000-1833000-performance

Then I unplug the AC-adapter and get the typical error message b/c my devices havent "settled"
cpufreqd_set_profile     : I haven't been able to set the chosen policy for CPU0.
I set 1833000-1000000-ondemand
System says 1000000-1000000-ondemand

Now, If I were to wait ~15 seconds, cpufreqd would set the correct frequency scaling. If I afterwards plug in the AC-adapter, cpufreq would return to the 1833000-1833000-performance policy

However, if I plug the AC-adapter back into the computer before cpufreqd sets the correct battery-power frequency/governor, then things go majorly wrong:
before unplugging, cpufeqd is in 1833000-1833000-performance governor + "AC ON" rule
right after unplugging, cpufreqd is in 1000000-1000000-demand governor + "AC ON" rule
  -the rule is still "AC ON" because the devices havent settled
If I plug in the AC-adapter before the devices "settle", cpufreqd matches the current rule "AC ON" to the desired rule "AC ON". Since they match, cpufreqd doesnt take any action. Processor remains at 1000000-1000000-demand governor + "AC ON" when plugged in.

/me annoyed : )

Do you get the same behavior ? Im thinking about posting this issue to the cpufreqd mailing list.

---

### Post by tehownt on 2008-11-15
Yes I indeed also get this strange behaviour...

I haven't had much chance to trigger the situation because I'm not really used to play much with the A/C adapter and just by waiting for cpufreqd to be able to set the correct frequency with A/C off you can go back to a normal mode when pluggin the A/C back on.

I'm sure though, that you'll get help from Mattia through the cpufreqd-user mailing list. Lemme know if he makes an update to fix that.

Also, if you use inotify, check the scaling_max_freq file access, it really is strange, when you plug the A/C back some process keeps on opening the file, but not when the A/C is unplugged.
I'd really like to know which process it is, but I'm out of ideas regarding which tool to use in order to know this.

---

### Post by mrpringle on 2008-12-17
I've been experiencing the exact same issue under gentoo.
[http://forums.gentoo.org/viewtopic.php?p=5318801#5318801](http://forums.gentoo.org/viewtopic.php?p=5318801#5318801)

I think the general consensus from the thread was that there's some BIOS functionality in the Dell XPS M1330 which causes the CPU to stay scaled down for about 16 seconds after the AC is unplugged. After this interval you can change to whatever valid freq you like, however during this time the CPU is locked to the minimum frequency.

Now of course the workaround in cpufreqd will work because it keeps trying to set the new frequency settings until they become effective.

If you look at my post you'll notice when the AC is initially unplugged there are two "processor cpux" acpi events ~16 seconds apart. The first one locks down the frequency and the second releases the lock so any valid frequency  can be chosen again.

A more intelligent way of cpufreqd working would be to detect the second processor cpu event
```

received event "processor CPU1 0000008000000000" 

```

before trying to apply new frequency settings, because they will just ignored for the first 16 seconds.


Now if you just want to use acpid instead to set your cpu scale / change governors you'll want to detect battery.*, ac_adapter.* and "processor CPU1 00000080 00000000" events.

---

