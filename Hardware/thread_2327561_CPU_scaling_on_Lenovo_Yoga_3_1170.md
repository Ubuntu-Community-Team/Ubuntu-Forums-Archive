---
title: "CPU scaling on Lenovo Yoga 3 1170"
date: 2016-06-12
forum: Hardware
---

### Post by stefan51 on 2016-06-12
Hi all,

I own a Lenovo Yoga 3 1170 convertible notebook with a core-m 5Y10c processor. With 16.04 (Gnome flavor) everything installs and runs fine except for one issue. The CPU which is slow in general (800MHz, but okay with turbo boost indicated up to 2GHz peaks) falls into a powersaving mode (500MHz unable to work with) once the battery reaches 25% and remains there until reboot even when recharging. A similar behavior has been reported on the Lenovo forums under windows (although "Throttlestop" seems to help). The bios is updated to the latest version.

I then disabled intel pstate driver by modifying /etc/default/grub (and running update-grub) to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=disable processor.ignore_ppc=1"

without processor.ignore_ppc=1 the problem remained even using the acpi-cpufreq this works to a certain extend. I however cannot load acpi-cpufreq with modprobe. There are no error messages but modinfo returns

$ sudo modinfo acpi-cpufreq
modinfo: ERROR: Module acpi-cpufreq not found.
$ sudo lsmod | grep acpi
snd_soc_sst_acpi       16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad               20480  0
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi



but scaling driver seems to be working anyways.

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver 
acpi-cpufreq

My remaining problem is that now the processor scales up at most to 1.0 GHz not to the 1.6 as in the specs (or 2GHz shown in the Gnome extension)

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1001000 1000000 900000 800000 700000 600000 500000 
$ cat /sys/devices/system/cpu/cpufreq/boost 
1


How can I obtain the correct frequencies and set them without risking to damage the notebook (boosting only short periods of time)?

Best wishes
Stefan

EDIT:
I tried setting scaling_max_freq manually without effect

$ echo -n 2000000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1001000

---

### Post by Doug S on 2016-06-12
Hi and welcome to Ubuntu forums.

Which version of Ubuntu are you using?

> **stefan51 said:**
> I however cannot load acpi-cpufreq with modprobe. There are no error messages but modinfo returns
Yes, probably because it is not a module, it is built in. (It depends on your kernel version, as Ubuntu has been messing with it being a module or built in.) 

> **stefan51 said:**
> My remaining problem is that now the processor scales up at most to 1.0 GHz not to the 1.6 as in the specs (or 2GHz shown in the Gnome extension)

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1001000 1000000 900000 800000 700000 600000 500000 
$ cat /sys/devices/system/cpu/cpufreq/boost 
1Are you sure? Note that when using the acpi=cpufreq driver: The frequencies listed are what were asked for, and not what they actually are; And 1001000 means turbo range is available, but nothing about how far into the turbo range it might be. Use turbostat (available via the linux-tools-common package) to know for sure what the CPU frequencies are.

It sounds as though your BIOS might be enabling clock modulation when the battery is low. Depending on the operational mode for your processor, the intel_pstate driver is incompatible with clock modulation, and it will get stuck at below the minimum frequency for the processor.

---

### Post by stefan51 on 2016-06-13
Thank you for the warm welcome.

It's been a long time since I (had to) invest so much time into getting hardware running :)
Good news first: I found a solution!

I followed your advice and tried out several things. 
Here is the output of turbostat:

with ACPI:
     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz
       -      24    1.75    1345     998
       0      28    2.12    1343     998
       2      16    1.18    1380     998
       1      33    2.62    1249     998
       3      17    1.09    1544     998


with pstate (above 25% battery):
     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz
       -    1596   80.10    1996     998
       0    1555   78.08    1996     998
       2    1420   71.27    1996     998
       1    1743   87.54    1996     998
       3    1664   83.54    1997     998


with pstate (below 25% battery):
     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz
       -     279   56.01     500     998
       0     292   58.60     500     998
       2     270   54.04     500     998
       1     271   54.41     500     998
       3     284   57.00     500     998

I tried setting also the clock modulation following the advices [here]("https://askubuntu.com/questions/624937/my-cpu-slows-down-after-a-while-and-does-not-recover/664333"). And it is pretty obvious that this is not the problem.
In a thread on a Lenovo [forum]("https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Yoga-3-11-CPU-stuck-at-0-48-Ghz-99-of-the-time/m-p/2231373/highlight/true#M35983") I found out that, apparently, the bios uses the "BD PROCHOT" flag to slow down the processor! 
Disabling this bit is said to not risk any damage, as the PROCHOT is still working, when the bidirectional communication is switched of. On the shell I did as described [here]("http://blog.patshead.com/2013/04/my-bios-is-limiting-my-cpu-clock-speed.html"):

sudo rdmsr -a -d 0x1FC
262239
262239
262239
262239
sudo wrmsr -a 0x1FC 262238


AND THIS WORKED! The notebook is back to full speed.

Two questions remain: 1) Why uses ACPI much slower frequencies 2) and what is the "suggested" way of not having to enter these commands always on the command line (cron or watch)?
Once setup, is it a good idea to write my experience on the supported hardware thread?

Thanks a lot, I already was afraid of having to buy another notebook!

PS: I'm using ubuntu (gnome) 16.04 64 Bit
Kernel: 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Doug S on 2016-06-13
> **stefan51 said:**
> Two questions remain: 1) Why uses ACPI much slower frequenciesYour CPU loads are very very different for your two listings. I assume these are just snapshots, and if you keep looking (taking more samples) you will observe both the acpi-cpufreq and intel_pstate (battery > 25%) CPU frequency scaling drivers adjusting CPU frequency as a function of load.

> **stefan51 said:**
>  2) and what is the "suggested" way of not having to enter these commands always on the command line (cron or watch)? I don't know.

It seems odd that your BIOS is using the PROCHOT bit this way. The "Intel® 64 and IA-32 Architectures Software Developer’s Manual" is surprisingly vague about the 0x1FC register. However, I think the way it limits the clock frequency is also via clock modulation.

---

### Post by achaw on 2016-12-10
Hi i have exactly the same problem. I'm using acpi right now but i can't set turbo to full speed.
I followed all your steps, but my max freq is still on 1ghz.  wrmsr seems to have no effect.
Can you help me?

```
sudo sudo rdmsr -a -d 0x1FC
262236
262236
262236
262236

```

```
sudo wrmsr -a 0x1FC 262236
```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1001000 1000000 900000 800000 700000 600000 500000
```

---

### Post by Doug S on 2016-12-10
> **achaw said:**
> I followed all your steps, but my max freq is still on 1ghz.  wrmsr seems to have no effect.
How do you know?
when using the acpi-cpufreq CPU frequency scaling driver, you only see frequencies the system asked for, which might not be what you actually get. You have to use turbostat to know for sure.

---

### Post by achaw on 2016-12-10
Well, same results...

```
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -      30    3.71     800     998
       0      31    3.84     800     998
       2      13    1.64     800     998
       1      17    2.12     800     998
       3      58    7.22     800     998
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -     344   43.12     800     998
       0     314   39.38     800     998
       2     292   36.54     800     998
       1     654   81.96     800     998
       3     117   14.62     800     998
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -     597   74.81     800     998
       0     592   74.12     800     998
       2     594   74.40     800     998
       1     607   76.08     800     998
       3     596   74.63     800     998
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -     429   53.77     800     998
       0     396   49.60     800     998
       2     404   50.63     800     998
       1     473   59.21     800     998
       3     444   55.65     800     998
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -     162   20.24     800     998
       0     150   18.78     800     998
       2     196   24.57     800     998
       1     141   17.71     800     998
       3     159   19.89     800     998
     CPU Avg_MHz   Busy% Bzy_MHz TSC_MHz
       -      15    1.92     800     998
       0      15    1.90     800     998
       2      23    2.85     800     998
       1      18    2.23     800     998
       3       5    0.68     800     998

```

---

### Post by Doug S on 2016-12-11
If your computer is indeed using the PROCHOT bit, as seemed to be indicated in the previous posts, then (I think) your clock duty cycle will be limited to 50%. I do not know if this will show in the clock modulation register or not, but can maybe check via, and for example (I do not have clock modulation enabled, so get 0):```
$ sudo rdmsr 0x19a -a
0
0
0
0
0
0
0
0

```If the PROCHOT bit is asserted by your hardware, I do not think clearing that register will work, but you could try it:```
sudo wrmsr 0x19a -a 0
```
EDIT: By the way, I believe that turbostat in debug mode will indicate if the PROCHOT bit is set:```
$ sudo turbostat  --debug sleep 10
```

---

### Post by achaw on 2016-12-11
Thanks man for all your answers, but yes prochot is disabled in BIOS.

```
sudo rdmsr 0x19a -a
0
0
0
0

```

I don't know what else to do....probably i'll give up...

---

### Post by achaw on 2016-12-18
Odd issue, i just format and reinstall Ubuntu. First, boot, install turbostat check...and THE SYSTEM IS SCALING! 
I think it was solved, so shutdown my pc. Today i launch turostat again and is STUCKED in 800 again....and i didn't touch anything in config...weird

---

### Post by achaw on 2016-12-22
Probably i found the problem. The cpu scales perfect when is plugged to AC. But, if it's on battery stucks at 800mhz.
How can i have the same behavior when my laptop is on battery?

---

### Post by achaw on 2016-12-23
With battery:

```
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 1 [OFF]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]

```

On AC;

```
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 0 [ON]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]

```

So the problem is turbo, is disabled while on battery. I try pstate-frequency with no luck:

```
 sudo pstate-frequency --set -t on 
**sh: printf: I/O error**
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 1 [OFF]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]
```

So...how can i change completely the power plans with intel_pstate? I just want performance with AC, and powersave on battery both with turb oenabled....

---

### Post by Doug S on 2016-12-23
> **achaw said:**
> With battery:

```
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 1 [OFF]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]

```

On AC;

```
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 0 [ON]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]

```

So the problem is turbo, is disabled while on battery.I do not think that is your root problem.

> **achaw said:**
> ```
 sudo pstate-frequency --set -t on 
**sh: printf: I/O error**
pstate-frequency version 3.7.2
    pstate::CPU_DRIVER   -> intel_pstate
    pstate::CPU_GOVERNOR -> powersave
    pstate::TURBO        -> 1 [OFF]
    pstate::CPU_MIN      -> 25% [500000KHz]
    pstate::CPU_MAX      -> 100% [2000000KHz]
```

So...how can i change completely the power plans with intel_pstate? I just want performance with AC, and powersave on battery both with turb oenabled....I think it is your BIOS that is disabling turbo and likely also doing something else resulting in limited performance.

Rather than use some tool, try using direct primitives  to control the driver:```
$ echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
```

---

### Post by achaw on 2016-12-24
Sadly, i can't modify that file....at all:

```
sudo echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
1
tee: /sys/devices/system/cpu/intel_pstate/no_turbo: Operation not permitted
```

I'm out of ideas here....also, i try Laptop Mode Tools with no luck...

---

### Post by Doug S on 2016-12-24
> **achaw said:**
> Sadly, i can't modify that file....at all:

```
sudo echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
1
tee: /sys/devices/system/cpu/intel_pstate/no_turbo: Operation not permitted
```

I'm out of ideas here....also, i try Laptop Mode Tools with no luck...Yes, if BIOS has turbo disabled, then you get that message. Here is my computer, but this time turbo is disabled in the BIOS:```
$ echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
1
tee: /sys/devices/system/cpu/intel_pstate/no_turbo: Operation not permitted
```EDIT: What do you get for this (example from my computer)?```
$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpufreq/policy0/*[/COLOR]
/sys/devices/system/cpu/cpufreq/policy0/affected_cpus:0
grep: /sys/devices/system/cpu/cpufreq/policy0/cpuinfo_cur_freq: Permission denied
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_max_freq:3400000
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_min_freq:1600000
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_transition_latency:4294967295
/sys/devices/system/cpu/cpufreq/policy0/related_cpus:0
/sys/devices/system/cpu/cpufreq/policy0/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpufreq/policy0/scaling_cur_freq:1599975
/sys/devices/system/cpu/cpufreq/policy0/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy0/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy0/scaling_max_freq:3400000
/sys/devices/system/cpu/cpufreq/policy0/scaling_min_freq:1600000
/sys/devices/system/cpu/cpufreq/policy0/scaling_setspeed:<unsupported>

```

---

### Post by achaw on 2016-12-25
Thanks! Turbo is enabled, in fact it works while is plugged into AC.

This is the output of the command:

```
/sys/devices/system/cpu/cpufreq/policy0/affected_cpus:0
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_cur_freq:800000
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_max_freq:2000000
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_min_freq:500000
/sys/devices/system/cpu/cpufreq/policy0/cpuinfo_transition_latency:4294967295
/sys/devices/system/cpu/cpufreq/policy0/related_cpus:0
/sys/devices/system/cpu/cpufreq/policy0/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpufreq/policy0/scaling_cur_freq:800000
/sys/devices/system/cpu/cpufreq/policy0/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpufreq/policy0/scaling_governor:powersave
/sys/devices/system/cpu/cpufreq/policy0/scaling_max_freq:2000000
/sys/devices/system/cpu/cpufreq/policy0/scaling_min_freq:500000
/sys/devices/system/cpu/cpufreq/policy0/scaling_setspeed:<unsupported>

```

---

### Post by Doug S on 2016-12-27
> **achaw said:**
> Thanks! Turbo is enabled, in fact it works while is plugged into AC.Yes, but I still think it is the BIOS that is holding it disabled when you are using battery. It is also strange to get such exact numbers for CPU frequency when using the intel-pstate driver (I do not recall ever seeing it before). So, it looks as though something (probably BIOS) is forcing pstate 8. We can check what was asked for verses what is actually given from looking at a couple of MSR registers:```
root@s15:/home/doug# modprobe msr
root@s15:/home/doug# rdmsr --bitfield 15:8 -d -a 0x198   [COLOR="#FF0000"]<<< gives what we are getting[/COLOR]
35
35
35
35
35
35
35
35
root@s15:/home/doug# rdmsr --bitfield 15:8 -d -a 0x199   [COLOR="#FF0000"]<<< gives what we are asking for[/COLOR]
37
37
37
37
37
36
37
37

```Note: in my example above, I was compiling a kernel, and so the computer was very busy. With all cores running my max pstate is 35, even though each core is actually asking for more.

---

### Post by achaw on 2016-12-28
Belive me, i'll check like a million times the bios and i can't dind anything related to the turbo while on battery.
This are the results of the commnads, compiling andoid kernel, on battery:

```
sudo rdmsr --bitfield 15:8 -d -a 0x198
8
8
8
8

```

```
sudo rdmsr --bitfield 15:8 -d -a 0x199
7
7
7
7

```

On AC:

```
sudo rdmsr --bitfield 15:8 -d -a 0x198
20
20
20
20

sudo rdmsr --bitfield 15:8 -d -a 0x199
17
18
5
20

```

---

### Post by Doug S on 2016-12-28
> **achaw said:**
> Believe me, I'll check like a million times the bios and i can't find anything related to the turbo while on battery.Yes, it just does it without it being anywhere in the settings.
> **achaw said:**
> This are the results of the commands, compiling android kernel, on battery:

```
sudo rdmsr --bitfield 15:8 -d -a 0x198
8
8
8
8

```

```
sudo rdmsr --bitfield 15:8 -d -a 0x199
7
7
7
7

```

On AC:

```
sudo rdmsr --bitfield 15:8 -d -a 0x198
20
20
20
20

sudo rdmsr --bitfield 15:8 -d -a 0x199
17
18
5
20

```Yes, so something other than the intel-pstate cpu frequency driver is forcing pstate 8 on battery.

---

### Post by achaw on 2016-12-30
Thanks alot for your help i'm giving up again right now....just test all variatons of my bios configs with no luck....also test another lunux distros (like arch) with no luck...

---

### Post by dhavalsonejii on 2017-08-31
Hi guys! Im going to be honest, I am a n00b but I also have the same yoga 3 11 and the same low battery cpu throttling which is *so annoying. *How would be the best way to stop this from happening. I have tried setting /sys/module/processor/parameters/ignore_ppc & ignore_tpc to 1 but this has had no effect. Any help to stop the throttling would be greatly appreciated!

---

### Post by Doug S on 2017-08-31
> **dhavalsonejii said:**
> Hi guys! Im going to be honest, I am a n00b but I also have the same yoga 3 11 and the same low battery cpu throttling which is *so annoying. *How would be the best way to stop this from happening.Beyond what has already been covered in this thread, I don't know. There seems to be plenty of complaints about it on the Lenovo forums (for example [here ]("https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll06_en/thread-id/28309")and [here]("https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll06_en/thread-id/34806/")).

---

### Post by alberto-o on 2018-01-17
> **stefan51 said:**
> I own a Lenovo Yoga 3 1170 convertible notebook with a core-m 5Y10c processor. With 16.04 (Gnome flavor) everything installs and runs fine except for one issue. The CPU which is slow in general (800MHz, but okay with turbo boost indicated up to 2GHz peaks) falls into a powersaving mode (500MHz unable to work with) once the battery reaches 25% and remains there until reboot even when recharging. A similar behavior has been reported on the Lenovo forums under windows (although "Throttlestop" seems to help). The bios is updated to the latest version.

I was experiencing the same problem with my Lenovo Yoga 3 11

> **stefan51 said:**
> In a thread on a Lenovo [forum]("https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Yoga-3-11-CPU-stuck-at-0-48-Ghz-99-of-the-time/m-p/2231373/highlight/true#M35983") I found out that, apparently, the bios uses the "BD PROCHOT" flag to slow down the processor! 
Disabling this bit is said to not risk any damage, as the PROCHOT is still working, when the bidirectional communication is switched of. On the shell I did as described [here]("http://blog.patshead.com/2013/04/my-bios-is-limiting-my-cpu-clock-speed.html"):

sudo rdmsr -a -d 0x1FC
262239
262239
262239
262239
sudo wrmsr -a 0x1FC 262238

AND THIS WORKED! The notebook is back to full speed.

This worked also for me, but I wanted to make it permanent. 
After some tests, I realized that the above command needs to be executed at boot time (after loading msr kernel module) and when resuming after suspend. 
I tested the following solution on Ubuntu 17.10, but I think it should work also on older versions.

```

sudo apt install msr-tools
sudo nano /etc/rc.local
```
put the following text:
```
#!/bin/sh
modprobe msr
sleep 1
/usr/sbin/wrmsr -a 0x1FC 262238 
```
save, exit, then:
```
sudo chmod 755 /etc/rc.local
sudo nano /lib/systemd/system-sleep/unlock-cpu-freq
```
put the following text:
```
#!/bin/sh
case "$1" in
        post)
          /usr/sbin/wrmsr -a 0x1FC 262238 
                ;;
esac
```
save and exit, then:
```
chmod 755 /lib/systemd/system-sleep/unlock-cpu-freq
```
reboot, and you're done!

---

