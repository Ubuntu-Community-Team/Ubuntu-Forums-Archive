---
title: "Scaling issues with Pentium M 1.7Ghz stuck at 600Mhz"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by Unicast on 2006-10-23
I'm at my wits end here trying to get scaling to work on my Dell D400 laptop. The processor is a 1.7Ghz Pentium M, but I can't get it to run any faster than 600Mhz.

I'm on a clean install of Edgy with the generic kernel and using KDE desktop environment.
```
2.6.17-10-generic
```

"cat /proc/cpuinfo" gives

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1700MHz
stepping        : 5
cpu MHz         : 600.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2
bogomips        : 1200.40
```

Contents of /etc/modules
```
lp
sbp2
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
speedstep-centrino
```

I've tried working through [this thread](http://www.ubuntuforums.org/showthread.php?t=248867&highlight=cpu+frequency http://www.ubuntuforums.org/showthread.php?t=248867&highlight=cpu+frequency) but still no joy!

This is driving me round the bend - any help would be gratefully received!

Uni.

---

### Post by Unicast on 2006-10-24
Bit more info...

 - Speedstep is enabled in the bios

 - This issue is with Edgy RC.

 - I'm also getting a "hw_random: RNG not detected" during the boot process.

Is there any way that I can maybe get the processor running at full whack without scaling back? That'd be better than being stuck at 600Mhz all the time. :(

Many thanks in advance. :D

---

### Post by Craigus on 2006-10-24
Have you been able to get CPU frequency scaling under any other version of Linux on this machine?

---

### Post by Unicast on 2006-10-24
> **Craigus said:**
> Have you been able to get CPU frequency scaling under any other version of Linux on this machine?

Not that I've noticed. I only noticed that the cpu was running at 600Mhz when I happened to look at the power management applet. I did however by messing around (can't remember what with now :???: ) get 1.7Ghz, and boy was Kubuntu snappy. But alas a reboot brought me back down to earth at 600Mhz. ](*,) 

I've just noticed there's a bios update (A08 - currently running A07) that was aimed at sorting out speedstep issues in windows 2000. I'll try that later and report back.

This is damn frustrating, I really want to stick with Kubuntu - everything (apart from speedstep) just works and it looks great!

Come on guys don't let me slip back to windoze!! ;)

---

### Post by Unicast on 2006-10-25
UPDATE:.......

Don't know what I did, but fired up the laptop last night and the power manager was reporting 1700Mhz!! :eek: 

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance
```

So I tries:
```
sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

and another...

```
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
ondemand
```

which allows the cpu cycles to fall and rise with the load. 8) 

All fixed now! :D

I was even more impressed when I found out that I can finally watch youtube videos with the sound and video in-sync with Flash 9. :D

I think I'm here to stay with Kubuntu for a good while longer!

---

### Post by mintcoffee on 2006-10-25
I'm encountering the same problem.. except I have a Pentium M 1.1GHz ULV. It seems related to bug #36014.

Is anything being done about this?

---

### Post by Unicast on 2006-10-26
I noticed the [Bug Report](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014) as well, and it looks like an ongoing issue.

If you google "scaling_max_freq" you'll notice a lot of reports on the web about scaling_max_freq = scaling_min_freq in /sys/devices/system/cpu/cpu0/cpufreq

This morning when I fired up my machine both the "scaling_max_freq" and "scaling_min_freq" = 600000 (0.6Ghz) and no scaling was going on, yet this evening "scaling_max_freq" = 1700000 and "scaling_min_freq" = 600000 :-k 

If anyone can shed any light on this strange behavior then I'm all ears!

---

### Post by Kateikyoushi on 2006-10-26
Did you do an update the day before ? I think it is a kernel related issue, when I start to use edgy my ULV Pentium M did not scale either it was always on max and really hot, then after an update it was solved.

---

### Post by Unicast on 2006-11-02
Back to 600Mhz again! ](*,) 

Anyone help me on this one?

Please?

---

### Post by Unicast on 2006-11-04
Ok, think I've cracked it! :mrgreen:

I downloaded and compiled a new kernel from source (yes me a complete newbie!) and used make xconfig before compiling to tell linux which processor I wanted to use - in my case Pentium M (centrino).

Compiled the kernel, copied my wireless card's firmware to /lib/firmware and rebooted.

Everything appears to be working fine so far! 

Many thanks to **linuxnewbie946** for his amazing How-To: [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

---

