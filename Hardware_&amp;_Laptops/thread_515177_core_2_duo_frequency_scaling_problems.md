---
title: "core 2 duo frequency scaling problems"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by ACGarib on 2007-08-01
Hi, I noticed that no matter what I do, typing  "cpufreq-info" in a terminal window gives me:
```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.

```

Notice the line that says the current policy is to be from 1.6GHz to 1.6GHz

I seems like no matter what, even if I play multiple HD videos at the same time, my cpu will always run at 1.6 GHz. I have a T7300 Core 2 Duo, and I am currently running on battery power if that matters.

Is there a way to chage the cpu scaling settings in ubuntu to get the full 2 GHz when I need it?

Ideally, my cpu would scale during battery use, but stay at full throttle when my laptop is plugged in.

Thanks

---

### Post by ACGarib on 2007-08-01
Now I've got a different problem. When I rebooted, I got a message saying that cpu frequency scaling is not supported. The only thing I changed was installing cpufrequtils so I could look to see if  frequency scaling was working.

How do I get CPU frequency scaling working again?

EDIT: Well, I've got CPU frequency scaling working again by installing powernowd then uninstalling it then installing cpufreqd.

Now I have a even worse problem -- I am stuck in 800 MHz mode.

How do I get proper CPU scaling when I am running off of the battery and no scaling when running on AC?

---

### Post by jet2230 on 2007-08-01
what is in your  /var/log/kern.log  ?

mine shows correct speeds, look for somethine like:

 CPU0: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Aug  1 19:35:49 bob kernel: [   12.426555] SMP alternatives: switching to SMP code
Aug  1 19:35:49 bob kernel: [   12.426726] Booting processor 1/1 eip 3000
Aug  1 19:35:49 bob kernel: [   12.437184] Initializing CPU#1
Aug  1 19:35:49 bob kernel: [   12.515387] Calibrating delay using timer specific routine.. 3466.96 BogoMIPS (lpj=6933925)
Aug  1 19:35:49 bob kernel: [   12.515395] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
Aug  1 19:35:49 bob kernel: [   12.515400] monitor/mwait feature present.
Aug  1 19:35:49 bob kernel: [   12.515404] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  1 19:35:49 bob kernel: [   12.515406] CPU: L2 cache: 2048K
Aug  1 19:35:49 bob kernel: [   12.515408] CPU: Physical Processor ID: 0
Aug  1 19:35:49 bob kernel: [   12.515410] CPU: Processor Core ID: 1
Aug  1 19:35:49 bob kernel: [   12.515412] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
Aug  1 19:35:49 bob kernel: [   12.515921] CPU1: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Aug  1 19:35:49 bob kernel: [   12.516391] Total of 2 processors activated (6936.95 BogoMIPS).

---

### Post by ACGarib on 2007-08-01
Here's some stuff from yesterday :

```


Jul 31 18:21:46 andrew-laptop kernel: [    9.015463] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Jul 31 18:21:46 andrew-laptop kernel: [    9.015470] monitor/mwait feature present.
Jul 31 18:21:46 andrew-laptop kernel: [    9.015471] using mwait in idle threads.
Jul 31 18:21:46 andrew-laptop kernel: [    9.015474] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 31 18:21:46 andrew-laptop kernel: [    9.015476] CPU: L2 cache: 4096K
Jul 31 18:21:46 andrew-laptop kernel: [    9.015478] CPU: Physical Processor ID: 0
Jul 31 18:21:46 andrew-laptop kernel: [    9.015479] CPU: Processor Core ID: 0
Jul 31 18:21:46 andrew-laptop kernel: [    9.015481] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Jul 31 18:21:46 andrew-laptop kernel: [    9.015488] Compat vDSO mapped to ffffe000.
Jul 31 18:21:46 andrew-laptop kernel: [    9.015491] Remapping vsyscall page to ffffe000
Jul 31 18:21:46 andrew-laptop kernel: [    9.015499] Checking 'hlt' instruction... OK.
Jul 31 18:21:46 andrew-laptop kernel: [    9.031379] SMP alternatives: switching to UP code
Jul 31 18:21:46 andrew-laptop kernel: [    9.031640] Early unpacking initramfs... done
Jul 31 18:21:46 andrew-laptop kernel: [    9.298094] ACPI: Core revision 20060707
Jul 31 18:21:46 andrew-laptop kernel: [    9.303490] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 31 18:21:46 andrew-laptop kernel: [    9.306834] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Jul 31 18:21:46 andrew-laptop kernel: [    9.306849] SMP alternatives: switching to SMP code
Jul 31 18:21:46 andrew-laptop kernel: [    9.306909] Booting processor 1/1 eip 3000
Jul 31 18:21:46 andrew-laptop kernel: [    9.317484] Initializing CPU#1
Jul 31 18:21:46 andrew-laptop kernel: [    9.395105] Calibrating delay using timer specific routine.. 3990.08 BogoMIPS (lpj=7980168)
Jul 31 18:21:46 andrew-laptop kernel: [    9.395110] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Jul 31 18:21:46 andrew-laptop kernel: [    9.395115] monitor/mwait feature present.
Jul 31 18:21:46 andrew-laptop kernel: [    9.395117] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 31 18:21:46 andrew-laptop kernel: [    9.395118] CPU: L2 cache: 4096K
Jul 31 18:21:46 andrew-laptop kernel: [    9.395120] CPU: Physical Processor ID: 0
Jul 31 18:21:46 andrew-laptop kernel: [    9.395121] CPU: Processor Core ID: 1
Jul 31 18:21:46 andrew-laptop kernel: [    9.395122] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Jul 31 18:21:46 andrew-laptop kernel: [    9.395734] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Jul 31 18:21:46 andrew-laptop kernel: [    9.395754] Total of 2 processors activated (7984.51 BogoMIPS).
Jul 31 18:21:46 andrew-laptop kernel: [    9.395953] ENABLING IO-APIC IRQs
Jul 31 18:21:46 andrew-laptop kernel: [    9.396148] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 31 18:21:46 andrew-laptop kernel: [    9.543026] checking TSC synchronization across 2 CPUs: passed.
Jul 31 18:21:46 andrew-laptop kernel: [    0.003998] Brought up 2 CPUs


```

And here's some stuff from now:

```


Aug  1 21:04:07 andrew-laptop kernel: [    9.615250] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Aug  1 21:04:07 andrew-laptop kernel: [    9.615256] monitor/mwait feature present.
Aug  1 21:04:07 andrew-laptop kernel: [    9.615258] using mwait in idle threads.
Aug  1 21:04:07 andrew-laptop kernel: [    9.615262] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  1 21:04:07 andrew-laptop kernel: [    9.615264] CPU: L2 cache: 4096K
Aug  1 21:04:07 andrew-laptop kernel: [    9.615266] CPU: Physical Processor ID: 0
Aug  1 21:04:07 andrew-laptop kernel: [    9.615267] CPU: Processor Core ID: 0
Aug  1 21:04:07 andrew-laptop kernel: [    9.615269] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Aug  1 21:04:07 andrew-laptop kernel: [    9.615277] Compat vDSO mapped to ffffe000.
Aug  1 21:04:07 andrew-laptop kernel: [    9.615280] Remapping vsyscall page to ffffe000
Aug  1 21:04:07 andrew-laptop kernel: [    9.615290] Checking 'hlt' instruction... OK.
Aug  1 21:04:07 andrew-laptop kernel: [    9.631154] SMP alternatives: switching to UP code
Aug  1 21:04:07 andrew-laptop kernel: [    9.631451] Early unpacking initramfs... done
Aug  1 21:04:07 andrew-laptop kernel: [    9.898230] ACPI: Core revision 20060707
Aug  1 21:04:07 andrew-laptop kernel: [    9.903623] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Aug  1 21:04:07 andrew-laptop kernel: [    9.907011] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Aug  1 21:04:07 andrew-laptop kernel: [    9.907027] SMP alternatives: switching to SMP code
Aug  1 21:04:07 andrew-laptop kernel: [    9.907088] Booting processor 1/1 eip 3000
Aug  1 21:04:07 andrew-laptop kernel: [    9.917702] Initializing CPU#1
Aug  1 21:04:07 andrew-laptop kernel: [    9.994870] Calibrating delay using timer specific routine.. 3990.12 BogoMIPS (lpj=7980254)
Aug  1 21:04:07 andrew-laptop kernel: [    9.994875] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Aug  1 21:04:07 andrew-laptop kernel: [    9.994879] monitor/mwait feature present.
Aug  1 21:04:07 andrew-laptop kernel: [    9.994882] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  1 21:04:07 andrew-laptop kernel: [    9.994883] CPU: L2 cache: 4096K
Aug  1 21:04:07 andrew-laptop kernel: [    9.994885] CPU: Physical Processor ID: 0
Aug  1 21:04:07 andrew-laptop kernel: [    9.994886] CPU: Processor Core ID: 1
Aug  1 21:04:07 andrew-laptop kernel: [    9.994887] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Aug  1 21:04:07 andrew-laptop kernel: [    9.995508] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Aug  1 21:04:07 andrew-laptop kernel: [    9.995528] Total of 2 processors activated (7984.69 BogoMIPS).
Aug  1 21:04:07 andrew-laptop kernel: [    9.995728] ENABLING IO-APIC IRQs
Aug  1 21:04:07 andrew-laptop kernel: [    9.995924] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  1 21:04:07 andrew-laptop kernel: [   10.142790] checking TSC synchronization across 2 CPUs: passed.
Aug  1 21:04:07 andrew-laptop kernel: [    0.003997] Brought up 2 CPUs


```


When I first installed cpufrequtils to see if cpu frequency scaling was working, it worked, but after I rebooted, everything got messed up.

That log file was huge, so I hope I copied the right stuff for you.

A couple of reboots ago, I noticed that daemon cpufreqd failed when I was shutting down.

thanks for you help,

Andrew




EDIT: well, I rebooted again and CPU scaling is not working again. My CPU is stuck at 2 GHz now. At least it is stuck at 2 GHz now instead of 800 MHz

---

### Post by jet2230 on 2007-08-01
from what your log says your cpu speed is fine, linux has no problen with that:

Aug  1 21:04:07 andrew-laptop kernel: [    9.995508] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Aug  1 21:04:07 andrew-laptop kernel: [    9.995528] Total of 2 processors activated (7984.69 BogoMIPS).


so problem will be with the program 'cpufreq-info'. i dont know why that is giving you the wrong reading i have not really used that app myself so cannot say. - how did u install cpufreq-info, best i can do is test it on my laptop and feed back?

---

### Post by ACGarib on 2007-08-01
cpufreq-info came with cpufrequtils. I installed cpufrequtils to see if cpu scaling was working on ubuntu. (at the time, I didn't know about the icon I could add to my panel that shows the same info)

I have uninstalled it and rebooted, but scaling was unsupported. I then tried reinstalling cpufreqd, but that still gave me the same scaling unsupported error. 

I noticed that when I reboot from terminal, I see some text saying "starting CPU Frequency daemon cpufreqd [fail]"

Also, when I type

```
 ps -A | grep cpufreqd 
```

I get nothing. If cpufreqd was running, I should get something.

I have been reading this thread for help: [ http://ubuntuforums.org/showthread.php?t=394911 ]( http://ubuntuforums.org/showthread.php?t=394911 )

Also, I tried doing this: [ http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html ]( http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html )

When I reconfigure it to be manually ajustable and I click on the icon, I see a small square (about 4 pixels by 4 pixels) appear under the icon, but clicking on the square does nothing.

I also tried going into gconf-editor and changing an option to show cpu scaling options in the power manager by doing this: [ https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/84297 ]( https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/84297 )

I am officially stumped.

Any other suggestions?

Thanks,
Andrew

---

### Post by jet2230 on 2007-08-01
this is the 1st 1 i tried from ur links: [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

worked perfectly. i didnt even know this could be done, i can chage the cpu frq freely.

u said that method did not work, why not? are you using beryl? i get that 4 x 4 pixal thing a lot in beryl, try refreshing the beryl window manager if you are using it.

---

### Post by ACGarib on 2007-08-01
No, that doesn't work. When I repackage the file then try to add the icon, an error pops up saying CPU scaling is unsupported. I then cllick on the icon and get the little square.

I am running compiz-fusion. I also tried running metacity, but I still get the little square.

typing

```


cd /proc/acpi/processor/CPU0


```

then

```


cat info


```

says that my cpu is scalable.

I am annoyed because it was working when I first installed cpufrequtils, but then it stopped working when I rebooted. Ever since then, things have been getting worse.

---

### Post by jet2230 on 2007-08-01
try: cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by jet2230 on 2007-08-02
> **ACGarib said:**
> No, that doesn't work. When I repackage the file then try to add the icon, ...


have u tried adding the icon 1st then repackaging? ( i suggest remove icon, repackage, add icon, repackage then check)

---

### Post by ACGarib on 2007-08-02
I tried the ```
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
``` 
but there is no such place. In fact, the whole cpufreq folder is not there. 

In the cpu folder, there is a text file named "sched_mc_power_savings", but when I try to open it, gedit says it can't be opened.

In the CPU0 folder, there is a text file named "crash_notes", but that is also not openable.

Your second suggestion of putting up the icon first did not help.

I just wish I could read that crash_notes file.

---

### Post by syko21 on 2007-08-02
whats the output of your
```
uname -r
```
?

---

### Post by ACGarib on 2007-08-02
```
 uname -r
```

gives me: 2.6.20-16-generic

I think that is the current kernel version.

I have an older kernel still in my boot menu, I dont know if I could boot into that to find the problem.

EDIT: I also tried ```
 lsmod | grep acpi 
```
and it gave me: ```
 pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi 
```

```
 lsmod | grep cpu 
```
gives me nothing. Neither does 
```
 sudo modprobe acpi-cpufreq 
```

If cpu frequency scaling is not supported, then those two commands should give me an error of some kind.

I guess I'm stuck somewhere between scaling working and not working.


EDIT # 2:

Well, if I go and type ```
 sudo cpufreqd 
``` THEN type ```
 lsmod | grep cpu 
```
I get the following:
```
 acpi_cpufreq           10056  2 
freq_table              5792  1 acpi_cpufreq
processor              31048  2 acpi_cpufreq,thermal 
```

and if I type: ```
 sudo modprobe acpi-cpufreq 
``` I still get nothing

So it appears that cpufreqd is not running on startup.


Wait... YES!! Adding the cpu frequency icon now gives me 1.2 GHz ! I guess cpufreqd is the key!

Let me do more testing (aka reboot several times with AC, battery, AC then battery, battery then AC, etc)

---

### Post by ACGarib on 2007-08-02
When I rebooted, I got the cpu scaling not supported error message again.

I tried doing sudo cpufreqd, but that didn't help. I also removed the frequency icon, then typed cpufreqd, then add the icon again, but that didn't help either.

I then tried doing exactly what I did before to get it working, but instead of it working, it is stuck at 800 MHz.

I noticed that doing ```
 lsmod | grep acpi 
``` now gives me : ```
 acpi_cpufreq           10056  2 
freq_table              5792  1 acpi_cpufreq
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
processor              31048  2 acpi_cpufreq,thermal 
```

typing ```
 lsmod | grep cpu 
``` now gives me: ```
 
cpufreq_powersave       2688  0 
acpi_cpufreq           10056  2 
freq_table              5792  1 acpi_cpufreq
processor              31048  2 acpi_cpufreq,thermal 
```

```
 sudo modprobe acpi-cpufreq 
``` still gives me nothing.

This just keeps on getting more and more confusing.




EDIT:

now doing ```
 sudo dpkg-reconfigure gnome-applets
``` and changing it to manual allows me to manually change between peformance and powersave. No matter which one I select, I still get 800 MHz though.

---

### Post by ACGarib on 2007-08-02
I hope this information will help:

When I first boot into ubuntu, scaling is not working. Cpu frequency daemon cpufreqd fails to load.

When I open a terminal and type ```
 cpufreq-info
``` I get the following: ```
 ~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```

If I then type: ```
 sudo modprobe acpi-cpufreq
``` Then try ```
 cpufreq-info
``` I will get the following: ```
 cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
```
This means modprobe acpi-cpufreq loads whatever program that controls scalilng. I am guessing it is cpufreqd.

If I unplug the laptop from the wall, then do ```
 cpufreq-info
``` I get the following: ```
 ~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
```

If I do cpu-info again a few seconds later I get: ```
 ~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
```

I don't know why it does that.

Notice the only cpufreq governors available are "performance".

If I type ```
 sudo modprobe cpufreq_ondemand
```
as well as the other governors, then do ```
 cpufreq-info
``` the new governors show up.

If I change the governor to ondemand by doing: ```
 sudo cpufreq-set -g ondemand
``` then do ```
 cpufreq-info
``` It shows the change in governors and it shows the speed as 800 MHz. If I play a 1080p video then do ```
 cpufreq-info
``` it reports the frequency as 2 GHz when I am plugged in to the AC power and when I am not.

So it seems like I have to do all of the above to get frequency scaling working every time I boot into linux.

Does anybody know how to get CPU frequency daemon cpufreqd to load and not fail during boot up?

This is the script that should run while the laptop is booting up: ```
 #! /bin/sh
### BEGIN INIT INFO
# Provides: cpufreqd
# Required-Start: $local_fs $syslog
# Required-Stop: $local_fs $syslog
# Should-Start:
# Should-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: start and stop cpufreqd
# Description: fully configurable daemon for dynamic frequency
#	 and voltage scaling
### END INIT INFO
# 
# Startup script for the cpufreqd daemon. It's been made using the
# skeleton example file to build /etc/init.d/ scripts.
# This file should be used to construct scripts for /etc/init.d.
#
# Written by Miquel van Smoorenburg <miquels@cistron.nl>.
# Modified for Debian GNU/Linux
# by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
# Version: @(#)skeleton  1.9.1  08-Apr-2002  miquels@cistron.nl
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/cpufreqd
CPUFREQD_CONFFILE=/etc/cpufreqd.conf
NAME=cpufreqd
DESC="CPU Frequency daemon"

# use lsb-base
. /lib/lsb/init-functions

# load defaults file
. /etc/default/cpufreqd

# abort if no executable exists
test -x $DAEMON || exit 0

#abort if no conffile exists
test -r $CPUFREQD_CONFFILE || exit 0

load_governor_modules() {
	case "$CPUFREQ_GOV_MODULES" in
		"") 
			return
		;;
		"auto")
			CPUFREQ_GOV_MODULES=$(cat /etc/cpufreqd.conf | \
						sed -ne 's/^policy=\([[:alpha:]]*\)/cpufreq_\1/p' | \
						uniq | xargs)
		;;
		*)
		;;
	esac
	modprobe -qa $CPUFREQ_GOV_MODULES || /bin/true
}

load_cpu_module() {
	if [ -n "$CPUFREQ_CPU_MODULE" ] ; then
		modprobe -q $CPUFREQ_CPU_MODULE || /bin/true
	fi
}

check_for_cpufreq_support() {
	# forget it if we're trying to start and no cpufreq found in kernel
	if !([ -d /sys/devices/system/cpu/cpu0/cpufreq ] || [ -f /proc/cpufreq ]) ; then
#		log_failure_msg "no cpufreq interface found. "
		return 1
	fi
	return 0
}

set -e

retval=0
case "$1" in
	start)
		log_daemon_msg "Starting $DESC" "$NAME"
		load_cpu_module
		load_governor_modules
		if check_for_cpufreq_support ; then
			start_daemon $DAEMON -f $CPUFREQD_CONFFILE
		else
#			log_failure_msg " Errors occurred starting cpufreqd"
			retval=1
		fi
		log_end_msg $retval;
	;;
	stop)
		log_daemon_msg "Stopping $DESC" "$NAME"
		if ( pidofproc $DAEMON 2>&1 > /dev/null ) ; then
			killproc $DAEMON 15
		fi
		log_end_msg $retval
	;;
#  reload|force-reload)
#      check_for_cpufreq_support
#      echo -n "Reloading $DESC configuration..."
#      start-stop-daemon --stop --oknodo --signal 1 --exec $DAEMON -- -f $CPUFREQD_CONFFILE
#      echo "done."
#      ;;
	reload|force-reload|restart)
		log_daemon_msg "Restarting $DESC" "$NAME"
		killproc $DAEMON
		sleep 1
		if check_for_cpufreq_support ; then
			start_daemon $DAEMON -f $CPUFREQD_CONFFILE
		else
#			log_failure_msg " Errors occurred starting cpufreqd"
			retval=1
		fi
		log_end_msg $retval;
	;;
	*)
		N=/etc/init.d/$NAME
		echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
		retval=2
	;;
esac

exit $retval 
```

The script is in /etc/init.d

I think this is what is failing during bootup. I just don't know what part of the script. Does anybody know where this log file is that the script writes to?

I also see other scripts related to scaling, such as cpufrequtils and powernowd. Do these interfere with cpufreqd and its startup script?







So, in summary, it seems like doing ```
 sudo modprobe acpi-cpufreq
``` enables cpu scaling. I then have to manually add the other governors and switch between them to get anything other than 2 GHz and 800 MHz.


Any and all help is appreciated.

Thanks, 

Andrew

---

### Post by raanan on 2007-08-02
Hi, 
I  am using 7.10  and had the same problem,  seems the file - /etc/init.d/cpufrequtils 

```

# Which governor to use. Must be one of the governors listed in:
#   cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
#
# and which limits to set. Both MIN_SPEED and MAX_SPEED must be values
# listed in:
#   cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
# a value of 0 for any of the two variables will disabling the use of 
# that limit variable.
#
# WARNING: the correct kernel module must already be loaded or compiled in.
# 
# Set ENABLE to "true" to let the script run at boot time.
# 
# eg:	ENABLE="true"
#	GOVERNOR="ondemand"
#	MAX_SPEED=1000
#	MIN_SPEED=500


```

is the one which fixes the scaling_max_freq and scaling_min_freq at boot time, I have changed 

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="0"
MIN_SPEED="0"
```

to - 

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="2133000"
MIN_SPEED="800000"
```

which fixed my problem of not able to change the CPU speed as this has inserted the same value into the min and max scaling limits making scaling not possiable after booting. 

you should enter your own min, max and governor. 

hopes this helps as i am running 7.10 here. .

---

### Post by ACGarib on 2007-08-02
my /etc/init.d/cpufrequtils looks different. Here's mine: ```
 #!/bin/sh
### BEGIN INIT INFO
# Required-Start: $local_fs
# Required-Stop:
# Default-Start:  2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: set CPUFreq kernel parameters
# Description: utilities to deal with CPUFreq Linux 
#	kernel support
### END INIT INFO
# 

DESC="CPUFreq Utilities"

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
CPUFREQ_SET=/usr/bin/cpufreq-set
CPUFREQ_INFO=/usr/bin/cpufreq-info
CPUFREQ_OPTIONS=""

# use lsb-base
. /lib/lsb/init-functions

[ -x $CPUFREQ_SET ] || exit 0

if [ -f /etc/default/cpufrequtils ] ; then
	. /etc/default/cpufrequtils
else
	ENABLE="false"
fi

# if not enabled then exit gracefully
[ "$ENABLE" = "true" ] || exit 0

if [ $MAX_SPEED -gt 0 ] ; then
	CPUFREQ_OPTIONS="$CPUFREQ_OPTIONS --max $MAX_SPEED"
fi

if [ $MIN_SPEED -gt 0 ] ; then
	CPUFREQ_OPTIONS="$CPUFREQ_OPTIONS --min $MIN_SPEED"
fi

#FAIL_MESG=""
if [ -n "$GOVERNOR" ] ; then
	#GOVERNOR=$($CPUFREQ_INFO -g | sed -ne "s/.*\($GOVERNOR\).*/\1/p")
	#if [ -n "$GOVERNOR" ] ; then 
		CPUFREQ_OPTIONS="$CPUFREQ_OPTIONS --governor $GOVERNOR"
	#else
	#	FAIL_MESG="governor not available"
	#fi
fi

CPUS=$(sed -ne 's/^processor[[:space:]]*: \([0-9]\+\)$/\1/p' /proc/cpuinfo)
RETVAL=0
case "$1" in
	start|force-reload|restart|reload)
		log_action_begin_msg "$DESC: Setting $GOVERNOR CPUFreq governor"
		for cpu in $CPUS ; do 
			# if [ $(CPUFREQ_INFO -a --cpu $cpu) -eq $cpu ] ; then
			log_progress_msg "CPU${cpu} "
			$CPUFREQ_SET --cpu $cpu $CPUFREQ_OPTIONS 2>&1 > /dev/null || RETVAL=$?
			# fi
		done
		log_action_end_msg $RETVAL "$FAIL_MESG"
		;;
	stop)
		;;
	*)
		echo "Usage: $0 {start|stop|restart|reload|force-reload}"
		exit 1
esac

exit 0

```


EDIT: I think you meant /etc/default/cpufrequtlis ? I have changed it, and I will reboot to see if it helped.

---

### Post by ACGarib on 2007-08-02
Unfortunately raanan, when I boot up I still get an error window saying that scaling is unsupported. 

After doing ```
sudo modprobe acpi-cpufreq
``` I can select the frequency manually, which is a big step foward, so thanks for the tip. 


So I guess I need to figure out how to get the above line of code to run or the equivalent during startup and before the little cpu speed icon is loaded.

I also need to figure out how to have the other governors load (only performance loads) during startup.

Also, what exactly does modprobe do? Does it just load programs? Is acpi-cpufreq even a program or is it a script? Sorry for all of the stupid questions.

---

### Post by ACGarib on 2007-08-03
I finally solved the problem.

I went into /etc/modules and added the following lines: ```
acpi-cpufreq
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
```

Now CPU scaling loads on bootup. 


EDIT: I also changed my /etc/cpufreqd.conf file. I uncommented the Ondemand High and Ondemand Low sections, then changed the options so it loads ondemand high when the battery is on high and medium and powersave low when the battery is running low. You can substitute whatever governors you want, but I feel these are the best compromises between battery life and performance.
/EDIT

Hopefully this thread will help others that have the same problem I had.

---

### Post by syko21 on 2007-08-04
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)
^^^ twas already solved

---

### Post by ACGarib on 2007-08-05
Just when I thought I had everything working how it should, it stops working! Now when I am on battery power, it stays at 800 MHz. when I do cpufreq-info, it says my current policy is "ondemand" and the frequency should be between 800 MHz and 800 MHz. When I plug in to AC power, it switches to performance @ 2 GHz. If I unplug it, it goes back down to 800 MHz. 

I found I can get around the 800 MHz problem by opening Mplayer and playing a HD video. This automatically switches the processor governor to performance, regardless of AC or battery power. I then close Mplayer, and the governor switches back to ondemand, but this time, ondemand works as it should (800 MHz to 2 GHz).

Any ideas on how to get "ondemand" working how it should without having to use Mplayer?

Grrrrrr... This is so fustrating!:mad:

---

### Post by ACGarib on 2007-08-19
Well, I wiped my HDD, installed Vista and Ubuntu, and to my suprise, CPU frequency scaling worked perfectly out of the box!

I have no idea why, but it did.

I though it might help some people if I told them this.

---

