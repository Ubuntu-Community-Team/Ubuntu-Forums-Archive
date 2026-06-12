---
title: "no cpufreq scaling in ibex"
date: 2008-10-30
forum: Hardware
---

### Post by tedrampart on 2008-10-30
I've been running ibex since the alpha stage, and part way though the upgrades I lost cpu frequency scaling.  

I have now tried reinstalling and am running the AMD64 version, and out of the box, it still doesn't do CPU scaling with either the commandline or the panel applet.

I have looked all over the forums, but can't seem to find any mention of this problem so far.  

my cpu is an Intel core2duo T7200, and worked with hardy and early ibex no problems.

when I run powernowd I get the following:
> powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]


/proc/cpuinfo shows both cores, with 6 steps listed..

 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies says this: > cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: No such file or directory

I've loaded the cpufreq_ modules, and nothing seems to have an effect on it.

when loading acpi-cpufreq module I get: > FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device


I figured that reinstalling would fix this issue, but I guess not.  I can try putting the regular version on here instead of the AMD64, and see if that has any result.

I'm at a loss right now... and could use some advice.

---

### Post by Cuppa-Chino on 2008-10-31
I went back in time to this thread from 2006 to get it working on my turion x2
[http://ubuntuforums.org/showthread.php?t=248867&highlight=amd+frequency+scaling]("http://ubuntuforums.org/showthread.php?t=248867&highlight=amd+frequency+scaling")

hope it helps you as well

---

### Post by tedrampart on 2008-10-31
thanks for the suggestion, but it was one of the first things I tried.  It still won't work because a bunch of the modules are no longer around, and "cpufreq" directories aren't found (eg. cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors: No such file or directory)  

I'm wondering if I should maybe just install the 32bit version again, and if that doesn't work I'm at a complete loss... it was working a couple weeks ago in the alpha stage without any setup at all.

---

### Post by tedrampart on 2008-10-31
thanks for the suggestion, but it was one of the first things I tried.  It still won't work because a bunch of the modules are no longer around, and "cpufreq" directories aren't found (eg. cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors: No such file or directory)  

I'm wondering if I should maybe just install the 32bit version again, and if that doesn't work I'm at a complete loss... it was working a couple weeks ago in the alpha stage without any setup at all.

---

### Post by tedrampart on 2008-10-31
solved.

I reinstalled, and deleted my /var and / partitions and re ordered them (not sure that contributed to it working now, but I did it since I was in there) and now it works.

maybe it was just a bad previous install..

---

### Post by BobCFC on 2008-11-16
Damn I have the same problem with the same errors when I run powernowd.

The fan has been running all the time even though my CPUs averages 4% use, it's only when I added the frequency scaling monitor applet to my panel that I realise scaling is not running at all, even though the box is still ticked in services.

---

### Post by BobCFC on 2008-11-16
YAY I fixed it!


It turned out when I reset my BIOS a few months ago the default setting had INTEL EIST disabled. I found it in the overclocking section of my bios. It turns out EIST stands for speedstep:

Enhanced Intel SpeedStep Technology 
[http://www.intel.com/cd/channel/reseller/asmo-na/eng/203838.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/203838.htm)

When I enabled it in BIOS then powernowd daemon starts properly and the CPU frequency scaling applets show that it has dropped to 66% as it should.. AND MOST IMPORTANT BLESSED PEACE FROM THE FAN lol

---

