---
title: "HowTo: Configure Cpu Frequency Scaling for Celeron M's with Control of the Governors"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by digitalbenji on 2007-10-19
OK, 
   This is not as simple as simply doing a ```
sudo modprobe p4_clockmod
```
   That will enable CPU frequency scaling, but it will not give you any useful control of the governors.  I found that the CPU would scale so low that the system would lose connectivity and become otherwise unresponsive and not useful.  
First, we will remove the powernowd daemon, because we are going to replace it with modules.
```
sudo apt-get remove powernowd
```
Next, we will install the cpufrequtils package, which allows us to set up cpu frequency scaling profiles that persist.  
```
sudo apt-get install cpufrequtils sysfsutils
```
Next, we want to figure out what frequencies are processor supports, but before we do that we need to load up cpufrequency scaling.  So we do this
 ```
sudo modprobe p4_clockmod
```
Then as quickly as you can, follow it with
```
sudo cpufreq-selector -g performance
```
This is to make sure the system does not scale down on us, making it too slow.
Now we are ready to find the CPU speeds that we want
, so do a:
```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 

```
This will give ouptut similar to this:
```
183332 366665 549998 733331 916664 1099997 1283330 1466663 
```
This is the range of frequencies, in Ghz (I think), that the processor supports.  I find that anything below 900mhz to 1ghz is just too slow, so I prefer not to scale below 1ghz.  Now we are ready to finish up:
```
sudo nano /etc/sysfs.conf
```
And add the following lines:
```
devices/system/cpu/cpu0/cpufreq/scaling_min_freq = 1099997
```
```
devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand
```
Now you will replace 1099997 with whatever the lowest value you want is.  The -d flag sets this as the lowest value to use.  Now, we need to set the system up to load the appropriate modules upon reboot.
```
sudo nano /etc/modules
```
and add these lines:
```
p4_clockmod
```
```
cpufreq_ondemand
```
```
cpufreq_performance
```
The performance governor keeps the CPU at its highest level, and ondemand scales it between the lowest we defined and the highest.  In my opinion, these are the two useful governors.  I keep my system in ondemand 90% of the time, but if I need some extra speed for a minute, I change the governor to performance. 
We can now have control the governors through the command line:
```
sudo cpufreq-selector -g ondemand
```
```
sudo cpufreq-selector -g performance
```
And the selected governor should persist until you change it!

Hopefully someone will find this helpful, as it was difficult to compile this information.  I have used this in both feisty and gutsy.  Add comments and I'll help if I can.

---

### Post by jmckean on 2007-12-03
Good stuff.  But I noticed that somewhere in this process my 2.0 GHz Pentium M suddenly got the top speed of 1.5 and I am not sure why.  Suggestions?

BTW, my goal is to have powernowd or cpufreqd manage my laptop's CPU and report to me via the applet.  Bottom speed might be an issue, I don't know, but heat and battery life are issues.  issue.

---

### Post by Ptero-4 on 2008-01-12
putting the p4_clockmod in /etc/modules crashes X (or it might be just gdm). It didn't happen in feisty but now it happens in gutsy.

---

### Post by HeWhoE on 2008-01-15
Worked great.  Thanks!

---

### Post by sebastjanp on 2008-02-04
Thank you very much. My scaling now works. I'm not sure what will happen after restart but sunce I set ondemand...

---

### Post by Vaan on 2008-02-21
... [B]THANK YOU!

[/B]I have seriously just spent a whole day trying to figure this out. I had the cpu scaling features working just fine under Feisty, and then I upgraded to Gutsy and they worked fine as well. I decided to do a fresh install of Gutsy today and could not for the life of me figure out what the hell was 'causing it not to work.

I spent most of the day searching the forums and google trying various things without luck, heck I wasn't even going to click on this thread because I do not have a celeron, I have HP that runs on a P4 chip. Little did I know a simple command of "sudo modprobe p4_clockmod" was all I needed to fix this damned issue of mine.

Man I am glad I decided to go ahead and see what this thread had to say, thanks again. Can't believe the other countless threads I looked at didn't even mention anything about the p4_clcokmod driver, instead I was trying to get acpi_cpufreq to work and was going nucking futs.

Glad that BS is done with. =P

---

### Post by kaziklcd on 2008-04-18
Hello to all :D
This is my problem with scaling my Intel Celeron
This is my cat /proc/cpuinfo
```
kazik@acer:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 22
model name      : Intel(R) Celeron(R) CPU          540  @ 1.86GHz
stepping        : 1
cpu MHz         : 1862.343
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3728.42
clflush size    : 64

```

When i typing third step ```
sudo modprobe p4_clockmod
``` im stuck with this...
```
kazik@acer:~$ sudo modprobe p4_clockmod
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.22-14-386/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

```

But p4-clockmod.ko is present in proper location.```
kazik@acer:/lib/modules/2.6.22-14-386/kernel/arch/i386/kernel/cpu/cpufreq$ dir
acpi-cpufreq.ko     longrun.ko      powernow-k8.ko         speedstep-smi.ko
cpufreq-nforce2.ko  p4-clockmod.ko  speedstep-centrino.ko
gx-suspmod.ko       powernow-k6.ko  speedstep-ich.ko
longhaul.ko         powernow-k7.ko  speedstep-lib.ko

```
What can i do to make my processor scalable? Thank for any advice!


Im working on Ubutu GG, Acer Extensa 5220

---

### Post by Bzyk on 2008-04-20
Celeron's M doesn't support for freq scaling!!! 
The posts above your's is only PrimaAprilis joke...

PS. Skoro procek nie supportuje freq scaling, to jak mo&#380;na za&#322;adowa&#263; modu&#322; jaja do tego celu? Bull ****.

---

### Post by tlyons on 2008-04-22
> **Bzyk said:**
> Celeron's M doesn't support for freq scaling!!! 
The posts above your's is only PrimaAprilis joke...

Odd.  Mine scales from 187 MHz to 1.5 GHz. :KS

---

### Post by kaziklcd on 2008-04-30
> **tlyons said:**
> Odd.  Mine scales from 187 MHz to 1.5 GHz. :KS

How?

---

### Post by @)--',------- on 2008-07-02
My Celeron M scales from 175 to 1400.

added p4_clockmod as a module, worked just fine.

I am using powernowd to govern scaling, but I am looking at other options.  The fans on my laptop are killing me. Every time it hits, 100% they spin up to jet fan speed. I hope to find a way to set a delay or adjust the tolerances.

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Celeron(R) M processor         1400MHz
stepping	: 5
cpu MHz		: 350.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
bogomips	: 699.93
clflush size	: 64

```

---

