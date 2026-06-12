---
title: "cpufreq Ubuntu 18.04"
date: 2018-07-14
forum: Hardware
---

### Post by denis.positron on 2018-07-14
Hi guys,

I like using cpufreq since Ubuntu 14.04, when I bought a Lenovo ThinkPad T440p (Intel Core i7-4600M CPU @ 2.90 GHz). I was able to configure cpufreq in a way that the Operational System started with the processor working at the minimum frequency. I usually leaved the processor at this low frequency until I needed more cpu power, when I could choose and change the frequency to a value in a list ranging from 0.80 GHz to 2.9 GHz or 2.9 GHz turbo mode.

I installed Ubuntu 18.04 LTS last week and since then I am exhaustively trying to make cpufreq to work. I installed indicator-cpufreq, cpufreqd, cpufrequtils, lm-sensors, psensor, sysfsutils. I tried to follow the instructions presented in

[https://ubuntuforums.org/showthread.php?t=2330427](https://ubuntuforums.org/showthread.php?t=2330427)

but it seems that sysv-rc-conf is not available in Ubuntu 18.04. Then I followed the instructions presented in the links below

[https://ubuntuforums.org/showthread.php?t=2356297](https://ubuntuforums.org/showthread.php?t=2356297)
[https://wiki.debian.org/HowTo/CpuFrequencyScaling](https://wiki.debian.org/HowTo/CpuFrequencyScaling)

but I had no success. I see the list of frequencies where I can click on the desirable value but the command

```
cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq
```

shows that the processor is always working at 2.9 GHz. If I run the command

```
cpufreq-info
```

I obtain the result

```
 analyzing CPU 0:
  driver: acpi-cpufreq
  ...
  available frequency steps: 2.90 GHz, 2.90 GHz, 2.70 GHz, 2.60 GHz, 2.40 GHz, 2.30 GHz, 2.10 GHz, 2.00 GHz, 1.80 GHz, 1.70 GHz, 1.50 GHz, 1.40 GHz, 1.20 GHz, 1.10 GHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 2.90 GHz and 2.90 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.90 GHz.
  ...

```

and the same result for CPUs 1, 2 and 3. 

After the commands

```
echo 'GOVERNOR="powersave"' | sudo tee /etc/default/cpufrequtils
sudo /etc/init.d/cpufrequtils restart 

```

I obtain

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq

```

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave
powersave
powersave

```

But the cpufreq-info says that the frequency is 2.9 GHz. After rebooting Ubuntu I obtain

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
performance
performance
performance
performance

```

Moreover, I am just using firefox, terminal (to perform commands like these above), nautilus and gedit, but the fan of my laptop is frequently working crazily fast.

I would appreciate very much any advice that you could provide to help me to make cpufreq to work properly.

Best regards,

Denis

---

### Post by kazakore on 2018-07-17
That's very odd, generally Ubuntu forces you to powersave/ondemand governor at boot and if you want to use a different one like performance you have to add/edit scripts to change it. I can't understand why you seem to be using performance governor as standard.

But I did also read a post on a mailing list the other day that stated Ubuntu has also changed the way it sets it (with a delayed timer method) so most the old ways of changing it don't stick any more. This is how it said to now do it (although I didn't do it this way and it seems to have worked with the method I used.)

> [SIZE=2]easiest place to look:
 /lib/systemd/set-cpufreq
 This is the way that ubuntu and probably debian set cpu governor today. 
 Notice that they do not include Performance, If Performance is wanted at 
 boot... the way to do that without getting errors when upgrading sw:
 create another file in the same directory maybe call it performance and 
 use the same code, but replace all governor choices with performance. Then 
 create a directory:
 /lib/systemd/system/ondemand.service.d
 in that directory create a file performance.conf will do and put some 
 lines like:
 ------------------------8<---------------
 [Service]
 
 ExecStart=
 ExecStart=/lib/systemd/performance
 ------------------------8<---------------
 Assuming the file you created was also called performance. The blank 
 ExecStart= is important as I found out, it resets Execstart to empty 
 first. Doing things this way has the advantage that 
 /lib/systemd/system/ondemand.service already makes sure the correct kernel 
 modules are loaded first and updates will go smoothly.[/SIZE]

---

### Post by kazakore on 2018-07-17
Mind

> 
 available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil

I always though Powersave for Intel and Ondemand was AMD but they basically performed the same role. I'm a little surprised to see so many governors for your CPU. What are you using?

---

### Post by denis.positron on 2018-07-17
Hi kazakore!

Thank you for your assistance. Following your instructions, in directory /lib/systemd/ I created a file called powersave with the same content of /lib/systemd/set-cpufreq but I replaced 

```

*interactive*)
                GOVERNOR="interactive"
*ondemand*)
                GOVERNOR="ondemand"

```

by
                
```
*interactive*)
                GOVERNOR="powersave"
*ondemand*)
                GOVERNOR="powersave"

```

I created a directory /lib/systemd/system/ondemand.service.d and in this directory I created a file powersave.conf with the content below

```
[Service]

ExecStart=
ExecStart=/lib/systemd/powersave

```

Then I rebooted the Ubuntu. But no changes occurred, i.e., the governor is still in performance and the frequency is still 2.9 GHz.

> I always though Powersave for Intel and Ondemand was AMD but they basically performed the same role. I'm a little surprised to see so many governors for your CPU. What are you using? 

I am using an Intel(R) Core(TM) i7-4600M CPU @ 2.90GHz:

```
 lscpu
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               60
Model name:          Intel(R) Core(TM) i7-4600M CPU @ 2.90GHz
Stepping:            3
CPU MHz:             2893.088
CPU max MHz:         2901.0000
CPU min MHz:         800.0000
BogoMIPS:            5786.01
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            4096K
NUMA node0 CPU(s):   0-3
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts

```

Are there more ideas about solving this issue? And should I undo the above procedure?

Thanks again!

Denis

---

### Post by kazakore on 2018-07-17
Although I've read it shouldn't do (like in that quote above) I've just checked and I'm still doing it through /etc/rc.local where I have added these lines and if I comment them out I'm back to the default powersave mode on boot.

```
#CPU governer and Min freq
 cpupower -c all frequency-set -g performance
 cpupower -c all frequency-set -d 2700000

```

As powersave/ondemand should be the default for Ubuntu finding out where you have somehow changed this would probably be a good idea.

Alternatively you could run a script at start-up with a sleep timer to switch back but that seems a rather messy solution...

---

### Post by Ice-Tea on 2018-07-18
[https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing](https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing)

Is the end of the above thermal driver anything to do with it or is it something different?

---

### Post by denis.positron on 2018-07-18
Hi guys,

Kazacore, thank you for your suggestion. I created a file /etc/rc.local with the lines

```
 #CPU governer and Min freq
 cpupower -c all frequency-set -g powersave
 cpupower -c all frequency-set -d 800000
```

and restarted the computer. No success yet.

> [https://www.phoronix.com/scan.php?pa...x-Driver-Axing](https://www.phoronix.com/scan.php?pa...x-Driver-Axing)

Is the end of the above thermal driver anything to do with it or is it something different?


I admire the people who maintain Linux alive, working and free. Hopefully somebody will assume such a noble responsibility.

Best regards,

Denis

---

### Post by Yellow Pasque on 2018-07-18
> Core i7-4600M

You're probably using intel_pstate driver, which works a bit differently than normal cpufreq driver. If you want full control over it, something like this may help: [https://github.com/pyamsoft/pstate-frequency](https://github.com/pyamsoft/pstate-frequency)
I don't have any recent Intel CPU's so I don't know a whole lot about it.

> Is the end of the above thermal driver anything to do with it or is it something different?

It's unrelated to the CPU frequency.

---

### Post by kazakore on 2018-07-19
> **Temüjin said:**
> You're probably using intel_pstate driver, which works a bit differently than normal cpufreq driver.

I knew I was using intel_pstate but all guides I had previously found still instructed setting via cpupower/cpufrequtils. From you comment I just found this document which helps explain why it never seemed to make as much difference as I thought it should....

[https://www.kernel.org/doc/Documentation/cpu-freq/intel-pstate.txt](https://www.kernel.org/doc/Documentation/cpu-freq/intel-pstate.txt)

Although even that page says to use cpupower to set the governor (but I don't think the set frequency limits works.)
> 
scaling_governor: This displays current active policy. Since each CPU has a
cpufreq sysfs, it is possible to set a scaling governor to each CPU. But this
is not possible with Intel P-States, as there is one common policy for all
CPUs. Here, the last requested policy will be applicable to all CPUs. It is
suggested that one use the cpupower utility to change policy to all CPUs at the
same time.

---

### Post by denis.positron on 2018-07-24
Hi guys,

Thanks again for the support. 

> 
You're probably using intel_pstate driver, which works a bit differently  than normal cpufreq driver. If you want full control over it, something  like this may help: [https://github.com/pyamsoft/pstate-frequency](https://github.com/pyamsoft/pstate-frequency)
I don't have any recent Intel CPU's so I don't know a whole lot about it.

I installed make, but 

```
sudo make edit
make: *** No rule to make target 'edit'.  Stop.

sudo make install
make: *** No rule to make target 'install'.  Stop.

```

Then I installed ubuntu-make

```
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt-get update
sudo apt-get install ubuntu-make
```

However I obtain

```
umake edit
usage: umake [--help] [-v] [-r] [--version]
             {android,dart,games,go,ide,kotlin,nodejs,rust,scala,swift,web}
             ...
umake: error: argument category: invalid choice: 'edit' (choose from 'android', 'dart', 'games', 'go', 'ide', 'kotlin', 'nodejs', 'rust', 'scala', 'swift', 'web')
```

So I am bashful because I was not able to run the first line of instructions...

---

### Post by Yellow Pasque on 2018-07-24
I'm not sure what you're doing with ubuntu-make?? You need the build-essential package installed. And you don't have to "make edit" if you just want to use the default build values, which you probably do:
```
git clone https://github.com/pyamsoft/pstate-frequency.git
cd pstate-frequency/
sudo make install
```

---

### Post by Doug S on 2018-07-24
> **kazakore said:**
> I knew I was using intel_pstate but all guides I had previously found still instructed setting via cpupower/cpufrequtils.From earlier posts, you are not using the intel_pstate driver, you are using the acpi-cpufreq driver. Why not?

Myself I never ever use any higher level tool to control the cpu frequency scaling driver, I just use the most primitive commands directly (which the higher level would have to use anyway).

---

### Post by Yellow Pasque on 2018-07-24
> **Doug S said:**
> From earlier posts, you are not using the intel_pstate driver, you are using the acpi-cpufreq driver.

I missed that (thanks for the catch). My apologies for leading you down the wrong path.

---

### Post by kazakore on 2018-07-25
> **Doug S said:**
> From earlier posts, you are not using the intel_pstate driver, you are using the acpi-cpufreq driver. Why not?

Myself I never ever use any higher level tool to control the cpu frequency scaling driver, I just use the most primitive commands directly (which the higher level would have to use anyway).

You're confusing me with the OP. Although I have to admit I also missed that the OP had shown he was using the acpi driver in his first post when another poster started talking about pstate so sorry for continuing with irrelevance.

---

