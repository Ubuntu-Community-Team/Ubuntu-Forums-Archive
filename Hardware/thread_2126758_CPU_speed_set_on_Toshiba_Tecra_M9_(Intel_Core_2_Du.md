---
title: "CPU speed set on Toshiba Tecra M9 (Intel Core 2 Duo)"
date: 2013-03-18
forum: Hardware
---

### Post by ontheair on 2013-03-18
Hello everyone!

I installed Xubuntu 12.10 on a laptop (Toshiba Tecra M9). Everything works nice, but the battery life is much shorter than on the previously installed Win XP. So i tried several ways to reduce power consumption (by the CPU in this case), but nothing worked for me:

_**Jupiter Applett**_
With this software I was able to change CPU speed (800 MHz, 1,2 GHz and 1,8 GHz) and some more. But the problem was, that Jupiter Applett caused the FS to be mounted just read-only when powered by battery. FS was correctly mounted while powered with AC. Strange thing. So I removed Jupiter Applett because of this problem.
Anyway, this software has stopped active development, so its maybe not a good idea to use in in new installations anymore.

_**cpufrequtils**_
The daemon (cpufreqd) crashes while starting and causes XFCE to generate a problem report. So I am not able to use any commands included in cpufrequtils.

_**CPU frequency controll in XFCE-starter**_
The starter is showing the actual frequency, but it can not be changed ("No CPU scaling driver available on your system").

I have no experiences on this topic (I used several Linuxes, but never before on laptops) and maybe I have done something terribly wrong. I would be very happy if I would get any suggestions!

CPU model: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz

Thank you!

---

### Post by Yellow Pasque on 2013-03-18
CPU scaling probably worked fine to begin with. I wouldn't assume that the CPU is to blame for higher power consumption (could be GPU or a combination of other things).
What is output of:
```
cat /proc/cpuinfo
lspci
```

---

### Post by dabl on 2013-03-18
More:

CPU frequency scaling is built into the kernel these days.  Check the output of

```
$ less /boot/config-`uname -r` | grep CPU_FREQ
```

on a default 12.10 system I see

```
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
```

---

### Post by ontheair on 2013-03-18
Hello, 

thank you for the answers!

Here are the informations requested:

cat /proc/cpuinfo

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping    : 13
microcode    : 0xa1
cpu MHz        : 1795.591
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm tpr_shadow vnmi flexpriority
bogomips    : 3591.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping    : 13
microcode    : 0xa1
cpu MHz        : 1795.591
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm tpr_shadow vnmi flexpriority
bogomips    : 3591.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

I just have internal graphics, no other GPU, so there should be not too much power consumption, hopefully.

less /boot/config-`uname -r` | grep CPU_FREQ

```
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y
```

Seems like frequency scaling is built in. Big question is, how can I use it correctly? Maybe I have to set the "gov_" configs mentioned above?

Again, thank you for your help, I would be happy if you can tell me a hint how to solve this!

---

### Post by speedfixer on 2013-03-19
You should be able to:

        cpufreq-set -c 0 -g ondemand && cpufreq-set -c 1 -g ondemand

(maybe sudo ...)

This sets both cores (before and after '&&') to 'ondemand' governor.

Then 'cpufreq-info' to verify.

(all assuming crefrequtils is still correctly.)

David

---

### Post by Doug S on 2013-03-19
My quess is that you do not have frequency scaling on that CPU. Below are two examples from two computers, one with frequency scaling and one without:```
doug@doug-64:~$  cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor: No such file or directory
``````
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
doug@s15:~/temp$
```And on the computer without frequency scaling, the config file has all of that stuff mentioned above (it just isn't relevant, when the CPU doesn't support it):```
doug@doug-64:~$ less /boot/config-`uname -r` | grep CPU_FREQ
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y

```

---

### Post by ontheair on 2013-03-20
Hello,

> You should be able to:
        cpufreq-set -c 0 -g ondemand && cpufreq-set -c 1 -g ondemand
(maybe sudo ...)

This resulted in a very general error message ("maybe you dont have enough rights, etc.") without any useful information. Of course I tried with sudo, so I had the rights.

> My quess is that you do not have frequency scaling on that CPU.

Hmm, when I used Jupiter Applet before, then frequency scaling was possible on that machine. I was able to change between "low power" (800 MHz), "high power" (always 1,8 GHz) and "ondemand" (changing cpu speed automatically to 800 MHz, 1,2 GHz and 1,8 GHz). The cpu speed was displayed correctly in gkrellm. I removed Jupiter Applet because it caused some other problems.
Ok, I will try to install Jupiter Applet again to get frequency scaling again and maybe I can solve the other problems caused by Jupiter.

> I wouldn't assume that the CPU is to blame for higher power consumption.
Maybe there are other devices in the machine with potential to save energy. The laptop consumes between 30 Wh and 35 Wh (depending on display brightness), which is way too much for the standard battery (48 Wh capacity).
If you can see anything in the lspci posted above, for more power saving, thank you for any suggestion!

---

### Post by Doug S on 2013-03-20
Ya, I saw that, not sure I believe it. Do the test I mentioned, then you will know for sure. Also, there is no need to use any add on program at all. If you want to set the governors to conservative or even powersave mode you can do it directly. Example scripts (use sudo):```
doug@s15:~/temp$ cat set_cpu_conservative
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "conservative" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

``````
doug@s15:~/temp$ cat set_cpu_powersave
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "powersave" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```Note: wait at least 1 minute after boot up, because of the /etc/init.d/ondemand script.

---

### Post by ontheair on 2013-03-20
I checked everything you wrote above - and then I found the mistake. I have to apologize, it was my mistake:

The BIOS battery was running low and the settings in the BIOS got lost. This also had an effect on the power safe settings provided by the BIOS. After replacing the battery and corrected the BIOS setting, the cpu scaling works again. Out of the box without additional software. By default it is working in "on demand mode", changing the cpu speed to 0,8 GHz, 1,2 GHz and 1,8 GHz on demand.

So the problem is solved now - although the machine still consumes more power than on the old MS operating system. But it's better now ;-)

Thank you for your help!

Edit: I wanted to mark the thread as solved, but there is no option visible when accessing the "thread tools". Am I missing something again?

---

### Post by Doug S on 2013-03-20
There is some problem with the new system and setting SOLVED. For the temporary how to, see [here]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730")

Glad you got it sorted out. Maybe try "conservative" mode for a little more power saving. You could also lock into the lowest frequency with "powersave" mode, for the minimum power use.

---

