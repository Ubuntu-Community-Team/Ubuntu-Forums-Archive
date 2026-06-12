---
title: "Ubuntu and overclocking"
date: 2008-09-02
forum: General Help
---

### Post by drewcoon on 2008-09-02
Hello!

I have Ubuntu installed on my rig with a 3.0Ghz Intel core 2 duo processor, and since I have amazing cooling and my motherboard supports it, I decided to overclock my FSB clock speed via the BIOS settings. I have it up to 3.33Ghz according to BIOS, but the problem I am facing is that when I check processor speed in terminal:

```
andrew@linbeast:~$ cat /proc/cpuinfo | grep -i Mhz
cpu MHz		: 3003.000
cpu MHz		: 3003.000
andrew@linbeast:~$ 
```

Ubuntu appears to be throttling my speed back down to the original 3.0Ghz? I've been using a panel app called "CPU Frequency Scaling Monitor", but it only has profiles for options ranging from 2.0Ghz up to 3.0Ghz.

I guess my question is basically, how can I create my own custom profile to stop Ubuntu from throttling my processor speed? I've tried disabling EIST in the BIOS (Something that allows the OS to control clock speed, I believe) but it still stays at 3.0Ghz. Can anyone help? Thanks in advance :)

---

### Post by ibuclaw on 2008-09-02
My guess is that that is the CPU state, not the actual total CPU speed.

As I have a 2.10GHz CPU, but I tend to leave it on idle, so when I run that same command, I get this as my output.

```
cpu MHz		: 800.000
cpu MHz		: 800.000
```
So I suspect some fruitless claims in your appeal.
I recommend that you try an app that actually reads what speed your CPU is running at.
Gnome offers a CPU freq scaling applet in the panel that can tell you that.

Regards
Iain

---

### Post by Tanker Bob on 2008-09-02
I assume that you are not running on a laptop. It looks like you are just reading the CPU's hardwired info. Something like lmsensors will tell you what your actual CPU speed is in realtime. It is in the repositories.

---

### Post by danwood76 on 2008-09-02
I have my little C2D (E6420 2.13GHz) clocked at 3.6GHz, whith my CPU frequency monitor it normally sits at around 2.5GHz as this is the idle power state.

When my system goes under load like compiling something or whatever it jumps up to 3.6.
You could try using something like cpuburn and watching the CPU frequency on the scaling monitor, just to check.
I would bet it is fine though.

---

### Post by drewcoon on 2008-09-02
> **tinivole said:**
> My guess is that that is the CPU state, not the actual total CPU speed.

As I have a 2.10GHz CPU, but I tend to leave it on idle, so when I run that same command, I get this as my output.

```
cpu MHz		: 800.000
cpu MHz		: 800.000
```
So I suspect some fruitless claims in your appeal.
I recommend that you try an app that actually reads what speed your CPU is running at.
Gnome offers a CPU freq scaling applet in the panel that can tell you that.

Regards
Iain

I've been using the panel app, and it doesn't give your your CPU speed, it just gives you a list of profiles (like performance and ondemand) that you can choose from to scale your CPU speed, and unfortunately the highest setting it goes to is only 3.0Ghz. So I'm wondering if it's possible to make a custom profile, or if it's all predefined.

Does "cat /proc/cpuinfo | grep -i Mhz" Actually get your clock speed, or just the speed that Ubuntu thinks it's running at? I've been rendering images in Blender to benchmark, and there doesn't seem to be a difference between having my BIOS overclocked or default, so came to the conclusion that my 3.3Ghz overclock is still running at 3.0Ghz.

---

### Post by drewcoon on 2008-09-02
> **Tanker Bob said:**
> I assume that you are not running on a laptop. It looks like you are just reading the CPU's hardwired info. Something like lmsensors will tell you what your actual CPU speed is in realtime. It is in the repositories.

When I use lm-sensors, I get

```
andrew@linbeast:~$ sensors
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.36 V
Vcore:       +1.13 V  (max =  +2.04 V)   
Vdimm:       +1.58 V
Vchip:       +1.17 V
+5V:         +5.12 V
12V:        +14.16 V
5VSB:        +4.70 V
3VSB:        +3.34 V
Battery:     +3.07 V
CPU:        2923 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +18.0°C  (high = +96.0°C, hyst = +92.0°C)  
                      (crit = +96.0°C, hyst = +92.0°C)  sensor = transistor
System:      +41.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

andrew@linbeast:~$ 
```

(Don't ask why there's no System fan RPM, I have a bunch of case fans set up with temperature probes).

It doesn't seem to give clock speed, just voltages and fan speeds. Am I using it wrong?

---

### Post by danwood76 on 2008-09-02
lmsensors reads the exact info you have above. (temps fan speeds etc)
I dont think it can do clock speeds.

The output from my OC'd system is similar to yours, I think the cpuinfo file displays the current CPU speed:
> 
danny@danny-desktop:/proc$ cat /proc/cpuinfo | grep -i Mhz
cpu MHz		: 2550.000
cpu MHz		: 2550.000


Im not sure how you list the processor speeds but I know its possible as I've done it before.

If your BIOS says your system is running at 3.3GHz then I would say that it is.

---

### Post by danwood76 on 2008-09-02
OK I just worked out how.

If you run the lshw command it will list all the available info about your system.
There will be one near the top labelled cpu, here is my output:

```

danny@danny-desktop:/proc/sys$ lshw
WARNING: you should run this program as super-user.
danny-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2046MiB

     *-cpu
          product: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
[B]          size: 3600MHz
          capacity: 3600MHz[/B]
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq

```

I've highlighted the speeds above to show you.
Hope it helps.

---

### Post by Tanker Bob on 2008-09-02
It looks like lmsensors is working fine. Not all motherboards are supported in every detail. Mine doesn't list many of the fan speed either. At least it's picking up your CPU fan speed, since that's the most important for overclocking.

I was wrong earlier, BTW. The command:

```
cat /proc/cpuinfo
```

will give you your current CPU speed. Sorry about that. I use KDE and hence KSensors to monitor the system. KSensors picks up the CPU speed. In my case, I'm overclocking a 2.40 GHz Core 2 Duo to 3.1 GHz, and that shows up fine in KSensors. Try this:

```
dmidecode | grep "Current Speed" | head -n 1
```

That should also give you your current CPU speed. This will give you your CPU's reported max speed:

```
dmidecode | grep "Max Speed" | head -n 1
```

For overclocking, of course, your current will be higher than your max. That's another way to get at the speed. Of the two console methods, using /proc/cpuinfo seems the most accurate.

That brings us back to your original problem. I'll have to think that one over for a few minutes.

---

### Post by drewcoon on 2008-09-02
> **danwood76 said:**
> OK I just worked out how.

If you run the lshw command it will list all the available info about your system.
There will be one near the top labelled cpu, here is my output:

```

danny@danny-desktop:/proc/sys$ lshw
WARNING: you should run this program as super-user.
danny-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2046MiB

     *-cpu
          product: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
[B]          size: 3600MHz
          capacity: 3600MHz[/B]
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq

```

I've highlighted the speeds above to show you.
Hope it helps.

```
*-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          [b]size: 3003MHz
          capacity: 3003MHz[/b]
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm cpufreq
```

No luck :(

Benchmarking with Blender also confirms that the processor is running at default speed. I restarted, went into BIOS and reset all my default CPU settings, then booted up Ubuntu and rendered and Image in blender. I then went back to BIOS, overclocked again, and rendered an image again to compare their render times. The difference between them is ~1 second, which means I'm definitely not overclocked.

@Tanker,

```
andrew@linbeast:~$ sudo dmidecode | grep "Max Speed" | head -n 1
	Max Speed: 3000 MHz
andrew@linbeast:~$ 
```

(My Current speed also shows the same, with CPU scaler set on "Performance")

My max speed is showing default, oddly enough. Did you need to do anything more other than raise your FSB speed in the BIOS settings to get that speed? Am I missing some kind of daemon or a system setting? My motherboard has a fancy "Linked" setting that lets you raise the FSB speed and it adjusts the memory speed proportionally, and that's what I've been using.

Thanks everyone for the help so far, by the way :)

Oh, and I have an MSI P7N Platinum mobo, very similar to yours Tanker :p

---

### Post by Tanker Bob on 2008-09-02
drewcoon,

Do you have powersaved installed? If so, try uninstalling it. It throttles the CPU.

---

### Post by drewcoon on 2008-09-02
> **Tanker Bob said:**
> drewcoon,

Do you have powersaved installed? If so, try uninstalling it. It throttles the CPU.

```
andrew@linbeast:~$ powersaved
The program 'powersaved' is currently not installed.  You can install it by typing:
sudo apt-get install powersaved
bash: powersaved: command not found
andrew@linbeast:~$
```

No, I don't have that installed.

But I noticed while looking in services that my CPU Frequency manager is powernowd, Could it be the issue? Is there a way to reconfigure / replace it?

---

### Post by Tanker Bob on 2008-09-02
Yep, that's also a CPU throttler. By default, the max is 80% and min is 20%. It defaults to "aggressive" CPU management. What is the status of your powernowd? Mine says that it starts at boot but is not running now. My CPU is running at 3.1GHz, so I believe the services screen.

You can try setting its max and min to 100% with:

```
sudo powernowd -u 100 -l 100
```

That may be the quickest and easiest resolution.

---

### Post by drewcoon on 2008-09-02
```
andrew@linbeast:~$ sudo powernowd -u 100 -l 100
[sudo] password for andrew: 
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
powernowd:   cpu0: 2003Mhz - 3003Mhz (4 steps)
powernowd:   cpu1: 2003Mhz - 3003Mhz (4 steps)
andrew@linbeast:~$ 
```

Hmm... No matter what I type in for the min and max, it doesn't exactly confirm that it's changing anything.

---

### Post by danwood76 on 2008-09-03
Does your POST screen (the screen you see when you first switch it on) confirm your overclock?
And also your BIOS?

---

### Post by drewcoon on 2008-09-03
> **danwood76 said:**
> Does your POST screen (the screen you see when you first switch it on) confirm your overclock?
And also your BIOS?

Both BIOS and POST confirm the overclock, the cell settings menu in the BIOS shows my cpu speed as 3.37Ghz, and during POST, it says something like:

```
Processor: Intel Pentium Core 2 Duo 3.0Ghz SPEED (speed as multiplier) = 3.37Ghz
```

So I have no doubt that my overclock is successful, I just can't figure out why Ubuntu won't acknowledge it :|

---

### Post by drewcoon on 2008-09-03
I found something else that look interesting,

```
andrew@linbeast:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: **2.00 GHz - 3.00 GHz**
  available frequency steps: 3.00 GHz, 2.67 GHz, 2.34 GHz, 2.00 GHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within **2.00 GHz and 3.00 GHz**.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: **2.00 GHz - 3.00 GHz**
  available frequency steps: 3.00 GHz, 2.67 GHz, 2.34 GHz, 2.00 GHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within **2.00 GHz and 3.00 GHz**.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
andrew@linbeast:~$
```

It says my hardware limit is 3.00 Ghz? Can it be reconfigured?

---

### Post by Tanker Bob on 2008-09-03
> **drewcoon said:**
> Hmm... No matter what I type in for the min and max, it doesn't exactly confirm that it's changing anything.
That's strange. I'm overclocking my E6600 and here's what I get from /proc/cpuinfo (in part):

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 3105.311
cache size      : 4096 KB
```

I don't understand why yours doesn't do that. Does your system say that powernowd process is currently running? The status on mine is "not running."

---

### Post by Tanker Bob on 2008-09-03
> **drewcoon said:**
> It says my hardware limit is 3.00 Ghz? Can it be reconfigured?
I think that your best bet is to ensure than none of those daemons are running. AFAIK, there's no need for them on a desktop system.

---

### Post by drewcoon on 2008-09-03
Okay, I've removed powernowd and replaced it with cpufreqd, which gives me total control over my CPU speed limit via the terminal. The only problem is that I still can't exceed 3.0Ghz.

I found some files,

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_min_freq
/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_max_freq

These seem to declare limits for each CPU core's highest and lowest clock speeds, but they are also system files that can't be edited, not even as root... I tried to 

```
sudo echo 3370000 > cpuinfo_max_freq
```

but I get a permission denied :(

I've been looking through some other pages, one that's a guide to CPU scaling in Ubuntu, and one an archived problem that's similar to mine... I'm still reading through them but here are the links,

[http://www.go2linux.org/how-to-configure-cpufreqd](http://www.go2linux.org/how-to-configure-cpufreqd)
[http://ubuntuforums.org/archive/index.php/t-421538.html](http://ubuntuforums.org/archive/index.php/t-421538.html)

EDIT uggh, I'm reading stuff about maybe having to compile my own kernel... Did you happen to install Ubuntu on your system *after* it was overclocked? Because I did the OS install a few months before I did the overclock.

Thanks for all the help by the way everyone, I appreciate it :)

---

### Post by herve34fr on 2008-12-09
Hi,
I've got exactly the same problem.
Processor AMD X2 2400Mhz @ 2820 Mhz (oc through the Bios).
My limit is given by cpuinfo-max_freq file  and is 2400 Mhz. Impossible to modify it.
My computer was allready OC when I installed Ubunto 8.10.
I've search on the web, but I don't see a solution. . .
Did you find something ?

Hervé

---

