---
title: "Core 2 Duo: Edgy only using one processor (+speedstepping problem)"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by psi36 on 2007-01-24
It seems Ubuntu is only using one of the processors in my HP nx7400 Core 2 Duo latop.
In the System Monitor I see only one processor, which isn't even working on the maximum available speed.

[IMG]http://zonk.be/img/SystemMonitor-1CPU.gif[/IMG]

I tried what is explained on [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400) under "To get the maximum speed out of the processor", but it's not working.```
# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1333000
# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1667000 1333000 1000000 
# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
cat: /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq: No such file or directory
# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies
cat: /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies: No such file or directory
```I did everything as explained, but I still only get 1.3 Ghz in stead of 1.6 Ghz.

Any ideas why I can see only 1 CPU in System Monitor and what I can do about it?

And what is there to be done about the speed stepping problem?

---

### Post by ronnieredd on 2007-01-24
I am by no means the expert here.
A couple of things I would look into though:
What's the output of ```
uname -a
```
I run the SMP version (Go to synaptics and search for the latest kernel that has "SMP" support.) In my case everything runs faster and everything that is supposed to see two CPU's, do.
My uname-a:
```
~$ sudo uname -a
Linux hostname 2.6.15-27-686 #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006 i686 GNU/Linux
```
Can't help you on the speedstep. Hope it helps on the processor numbers though.

---

### Post by RandomJoe on 2007-01-24
Edgy is supposed to use an SMP kernel by default ("generic" I believe it's called).  Did you select a different kernel?  That would explain both why you don't see the second CPU and why you don't have the cpu1 directory under sys.

On the Speedstep, which governor is the system using?
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

I don't know for sure about Edgy, but Dapper defaults to 'userspace'.  That means the 'powernowd' daemon is running.  If that is your setup and you just want the thing to run full speed all the time, just kill powernowd.  Restarting it will reinstate speed control.  But if you start a processor-intensive task it should scale up the speed just fine.

There are a few other governors available (cat "scaling_available_governors" to see what's loaded on your system).  You can have the system use a different one if you want, each has its own characteristics as to when it will speed up or slow down (also one just stays fixed at max, one at min).

---

### Post by psi36 on 2007-01-24
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
```

---

### Post by virtual_void on 2007-01-24
What is the output from
# cat /proc/cpuinfo

Should look like  this for a Core2

# cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3663.18

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3657.84


This is my work laptop which is running Edgy (Kubuntu). Both cores work fine and all frequencies (1.00 1.33, 1.83 GHz) works. I have not installed anything special.
However, speedstep for Core2 did not work properly in Dapper.

I guess that you see both cores in Windows (if you have that installed, I don't), but it might be worth looking at the BIOS setting to see if there is something there that has to do with multiple cores. Linux has to be informed about how many cores you have and it will (normally) bring all available cores online during boot.

---

### Post by psi36 on 2007-01-25
```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.00
```

---

### Post by harrisony on 2007-01-25
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
try that
or in short
sudo apt-get install linux-generic

---

### Post by u-blunt-2 on 2007-01-25
I have the same problem. I installed linux-generic and linux-686-smp, reboot, get linux-2.6.17-10-386 and linux-generic in GRUB.
However, i can't load linux-generic (it gives me x-server problem when it loads GDM). the 2.6.17-10-386 is default. 

uname -a
```
 
Linux XEUS 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux
```

cat /proc/cpuinfo
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2399.986
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4804.14

```

Oh yeah... Both processors were detected in AMD64 Ubuntu and, from what I remember, my previous install of 6.06....

---

### Post by psi36 on 2007-01-26
> **virtual_void said:**
> I guess that you see both cores in Windows (if you have that installed, I don't), but it might be worth looking at the BIOS setting to see if there is something there that has to do with multiple cores. Linux has to be informed about how many cores you have and it will (normally) bring all available cores online during boot.

In my Windows Task Manager I do see two processor graphs, so there the two processors are working: [http://zonk.be/img/WindowsTaskManager.GIF](http://zonk.be/img/WindowsTaskManager.GIF)

---

### Post by psi36 on 2007-01-26
I did 
sudo apt-get install linux-generic
and
sudo apt-get install linux-686-smp

So now I'm running
```
# uname -a
Linux dimi-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
```

And I have two processors, also in System Monitor:
```
# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.19

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3325.04
```

But they're still not working full speed, only 1.3 Ghz, in stead of 1.6:```
# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1333000
```

Although I did (as described on [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400):](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400):)
```
# sudo -s
# echo 1667000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
# echo 1667000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
```

---

### Post by psi36 on 2007-01-31
OK, I've got both processors running now, but there's still the speedstepping issue.
Anyone any suggestions how to fix this?

```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1333000
$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
1333000
```

---

### Post by psi36 on 2007-04-12
Problem seems to be solved:```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1667000 1333000 1000000 
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1667000
$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
1667000
```
Can't remember what I did to solve this. Just checked it again today and now I do get 1.67Ghz as maximum frequency...

---

