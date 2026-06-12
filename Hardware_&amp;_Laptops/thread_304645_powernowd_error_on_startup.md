---
title: "powernowd error on startup"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by dumbkiwi on 2006-11-22
I'm having issues with my cpu and fans, and have been wondering whether the cpu scaling is working properly.  When I try to start the powernow daemon, I get the following:

```
sudo /etc/init.d/powernowd restart
 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...                                                        
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported
                                                                         [ ok ]
```

Clearly the relevant sys files/directories have not been created.  Anyone know what the problem might be here, and how to fix it?

Cheers

Matt

---

### Post by zgornel on 2006-11-22
System specs ?

---

### Post by dumbkiwi on 2006-11-22
cpu is an intel core duo running on kubuntu 6.10.  Not sure what other specs are relevant.

---

### Post by zgornel on 2006-11-22
After a reboot try *cat /proc/cpuinfo* and see the frequency of the processor. Then *ps -aux |grep powernowd* and check if powernowd is running. If it is running and the processor frequency is lower, everything is ok. Why are you restarting the daemon ? I tried to restart it, it worked but it wasn't anymore in the process list and the processor scaled down. Seems like some bugs lie around in this area. BTW, what kernel and ubuntu version are you running ?

---

### Post by dumbkiwi on 2006-11-22
/proc/cpuinfo shows both cores running at full speed 
```
cpu MHz         : 1662.807
```
the powernowd daemon is not running when checking ps aux.
uname -a gives:
```
Linux matt-laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
```
I am assuming that "SMP" means that the kernel understands intel core duo.

I purged powernowd, and installed cpufreqd to see if that would work, however on startup, that errors with:
```
No cpufreq interface found, not starting cpufreqd.
```
however, the relevant modules seem to be loaded:
```
matt@matt-laptop:~$ lsmod | grep cpu
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
```
However, if I try to load the speedstep-centrino module, I get:
```
matt@matt-laptop:/lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq$ sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
```

Anyone got any other ideas?

---

### Post by zgornel on 2006-11-22
Go to /lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq/ and see if the speedstep_cetrino.ko is present. If not, recompile kernel or I can attach my speedstep_centrino.ko and you can try inserting it :D

---

### Post by dumbkiwi on 2006-11-22
It's definitely there:
```
matt@matt-laptop:~$ ls /lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq/
acpi-cpufreq.ko     longrun.ko      powernow-k7.ko         speedstep-ich.ko
cpufreq-nforce2.ko  p4-clockmod.ko  powernow-k8.ko         speedstep-lib.ko
gx-suspmod.ko       powernow-k6.ko  speedstep-centrino.ko  speedstep-smi.ko
```
If you look at the error when trying to load the module, it says it can't find the device.  So either my cpu is incompatible with the speedstep-centrino module, or there's something else going on.

---

### Post by zgornel on 2006-11-23
Have you tried looking into the bios for a similar setting? Enabling speedstep or something ? It might be an incompatibility of the kernel with the Chipset.

---

### Post by dumbkiwi on 2006-11-23
I couldn't find any relevant settings in the bios sadly.

---

### Post by zgornel on 2006-11-23
The last resort would be to compile the kernel yourself. Is it working in Windows ?

---

### Post by dumbkiwi on 2006-11-24
hmmmm.  Not sure how compiling my own kernel would help, unless I compiled an updated kernel.  However, I'm not sure I want to run with a vanilla kernel.  I've compiled a lot of kernels on various gentoo machines, however, they were always patched with various bits and pieces that the gentoo devs deemed necessary.

Also, I've not tried that machine on windows, as I don't use windows, and don't own any licenses.

---

### Post by zgornel on 2006-11-24
I think the vanilla kernel and ck patch in somewhat equivalent to the ubuntu kernel. Wait for the final 2.6.19 and respective ck patch and try them. The differences are minor and you can see them if you copy the config-<kernel ver> from /boot as .config and run make xconfig. I suspect the newer intel chipsets for duo aren't quite supported in older kernels.

---

