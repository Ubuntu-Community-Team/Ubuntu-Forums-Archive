---
title: "Powernowd fails to start with coppermine cpu"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by Chrissss on 2005-10-10
Hi!

I'm trying to get speedstepping to work. I've got a Siemens Lifebook e-6570 Notebook with a PIII 750mhz (Coppermine) CPU. Those CPUs support afaik basic speedstepping. But when i try to start powernowd, it fails
```
stein:~$ sudo powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
```
Here's the info about the cpu: 
```
stein:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 6
cpu MHz         : 598.498
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1175.55
```
Inside the acpi settings there are the throtteling infos. Looks like the CPU should have a couple of modes:
```
stein:~$ cat /proc/acpi/processor/CPU0/throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
```

While searching for a solution, i found that the speedstep modes should be listed in /sys/devices/system/cpu/cpu0, but it's empty
```
stein:/sys/devices/system/cpu/cpu0$ ls -al
insgesamt 0
```
Inside a [Gentoo Forum](http://www.mepislovers.org/modules/newbb/viewtopic.php?forum=11&topic_id=2511) i found out that i need the speedstep-smi module for my cpu, but it won't load
```
stein:~$ sudo modprobe speedstep-smi
FATAL: Error inserting speedstep_smi (/lib/modules/2.6.12-9-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko): No such device
```
Instead of speedstep-smi there's another module loaded: speedstep_lib
```
stein:~$ lsmod | grep speedstep
speedstep_lib           4228  0
```
Has someone an idea to get speedstep to work?

Thanks
 Christoph

---

### Post by blackpaw on 2005-10-23
*waves*

same problem here.. any ideas?

---

### Post by Chrissss on 2005-10-23
I tried everything. Nothing worked out yet. There's a bugzilla entry on bugzilla.ubuntu.com but no solution:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=4262](https://bugzilla.ubuntu.com/show_bug.cgi?id=4262)

Perhaps adding some options to speedstep-smi helps, like described inside the bugzilla entry,

sudo modprobe speedstep-smi smi_port=0xb2 smi_cmd=0x82 smi_sig=1

or perhaps this wiki

[http://thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_Thinkpads](http://thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_Thinkpads)

CU
 Christoph

---

### Post by blackpaw on 2005-10-24
*lol*

I like:
> APPLYING THIS HOWTO MAY MAKE YOU DUMB, CRASH YOUR CPU, YOUR MOTHERBOARD, MAKE YOUR GIRLFRIEND LEAVE YOU, OR MAYBE WORSE, USE IT AT YOUR OWN RISKS.....

but I would really like powernowd.. or maybe cpufreqd - to stay with ubuntu (and not break dependencies)

As it looks, Intel has never given out the full specs on this particular chipset (PIIx4E/440MX/Coppermine)

He 
[http://www.poupinou.org/cpufreq/speedstep-piix4.html]("http://www.poupinou.org/cpufreq/speedstep-piix4.html")
seems to have succeeded, but what he writes is too advanced for me to understand... :(

can anyone help?

---

### Post by Chrissss on 2005-10-25
Hm, i don't know, that stuff is very old...

"For kernel 2.5 and 2.6-test", The 2.6 kernel is out for quite some time. I doubt that those patches will help us now.

CU
 Christoph

PS: YESSSS!!!

I got it, at least at my pc. Make a dry run first, remove speedstep-lib and speedstep-smi and reload them with the following options

modprobe -r speedstep-lib
modprobe -r speedstep-smi
modprobe speedstep-lib relaxed_check=1
modprobe speedstep-smi smi_port=0xb2 smi_cmd=0x82 smi_sig=1

Now restart your powernowd

/etc/init.d/powernowd restart

Does it work? If yes, add those two files to /etc/modprobe.d/

/etc/modprobe.d/speedstep-lib.modprobe
options speedstep-lib relaxed_check=1

/etc/modprobe.d/speedstep-smi.modprobe
options speedstep-smi smi_port=0xb2 smi_cmd=0x82 smi_sig=1

And finally add those two line to your /etc/modules 
speedstep-lib
speedstep-smi

After that or a reboot speedstep works here! Don't be confused powernowd throttels your cpu to the low setting, only when you actually use your cpu (e.g. while compiling) the cpu is set to full speed.

---

### Post by blackpaw on 2006-01-04
:( 

I don't have either speedstep-smi or speedstep-lib

Any hint where I can get it from?

Update: It must be compiled into the Kernel as a module... so far so good but I still miss one thing...
[http://ubuntuforums.org/showthread.php?p=629336#post629336](http://ubuntuforums.org/showthread.php?p=629336#post629336)

---

