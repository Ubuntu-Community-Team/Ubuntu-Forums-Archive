---
title: "Bad CPU frequency scaling on Thinkpad T540p - Heat problems"
date: 2016-05-15
forum: Hardware
---

### Post by Aquignis on 2016-05-15
Hi everyone,

I have recently installed Ubuntu on my T540p without success: the  issue is that the CPU keeps on overheating (80 °C with the sensors command) and seems to get stuck at 2.5 GHz, even if the only thing opened in my session is a terminal. The battery life is around 3 hours when the computer is idling (instead of way more under Windows).
The CPU is an Intel i7-4710MQ. I also have a NVIDIA GT730M in the  laptop.
I haven't met this issue on Windows during the few months I've had the computer.

Disable the card via bbswitch does not solve to the problem (my power consumption decreases from about 2 W and is around 25 W). To do this, I had to rmmod the nouveau driver and set acpi_osi=Linux (see [this]("https://github.com/Bumblebee-Project/bbswitch/issues/112")) in the kernel parameters. optirun and Bumblebee do not work, but I think that this is not the problem here.

I have set Intel SpeedStep and other power management options on "Battery optimized" or "Balanced" in the BIOS.

The only thing that helped was manually setting the  frequency to a low value, which increased the autonomy and resulted in normal temperatures at the cost of  performance.

I would appreciate any help.
Thanks for reading !

([cross-posted]("https://bbs.archlinux.org/viewtopic.php?pid=1625299") from Arch Linux forums, despite I think that posting everywhere is not a good idea)

---

### Post by Linuxisfast on 2016-05-15
Ubuntu 14.04 with i7 4790     [http://imgur.com/NUpexAw](http://imgur.com/NUpexAw)

Under Arch due to Config Hz=300 issue of kernel, the CPU core are near turbo all the time rarely dropping even under idle and the temp shoots up to four to five degrees on average over Ubuntu or SUSE kernel where the number is 250.

---

### Post by Linuxisfast on 2016-05-15
[http://imgur.com/X3LfQQM](http://imgur.com/X3LfQQM) this is latest 16.04 on my ThinkPad x220 with i5 Sandybridge, again CPU scaling working as it should.

---

### Post by Aquignis on 2016-05-15
On your first screenshot, your i7 4790 was working at rather high frequencies. But it is a desktop processor, right ? Was your computer under idle ?
On your second screenshot, everything seem to be working properly (supposed that you are under idle).

As I said before, this is not my case. I'm running all time at 2.5 GHz or more...

---

### Post by Linuxisfast on 2016-05-15
> **Aquignis said:**
> On your first screenshot, your i7 4790 was working at rather high frequencies. But it is a desktop processor, right ? Was your computer under idle ?
On your second screenshot, everything seem to be working properly (supposed that you are under idle).

As I said before, this is not my case. I'm running all time at 2.5 GHz or more...

The Haswell usually runs high compared to Sandybridge but if you notice, one of the core has hit close to the low of 800MHz, now compare that in Arch and you will see all cores running on turbo. In your case, it seems you are suffering from the Arch issue even with Ubuntu kernel. Something in your system is driving it up. Can you post a screenshot of your system with i7z?

---

### Post by Aquignis on 2016-05-15
I have heard of this kernel problem on the Arch's forums topic.

It's hard to compare your Sandy Bridge CPU with your Haswell one, because the difference between both screenshots is high, but, anyway, thanks for the information (I did not know that Haswell was usually more excited than other architectures).

You will find what remains in the terminal after running i7z [here](http://pastebin.com/TS75bqNV) and the in real time monitoring [here](http://imgur.com/lruYsvy).

---

### Post by Linuxisfast on 2016-05-15
Have you installed intel microcode btw?

---

### Post by Aquignis on 2016-05-15
I did not install it manually, but I think that everything is OK:
[FONT=lucida console]```
[COLOR=#000000]$  sudo modprobe cpuid && sudo iucode_tool -tb -lS  /tmp/micro/
iucode_tool: system has processor(s) with signature  0x000306c3
selected microcodes:
001: sig 0x000306c3, pf mask 0x32, 2015-08-13, rev 0x001e, size 21504


$ dmesg | grep microcode
[    2.275163] microcode: CPU0 sig=0x306c3, pf=0x10, revision=0x1f
[    2.275463] microcode: CPU1 sig=0x306c3, pf=0x10, revision=0x1f
[    2.275873] microcode: CPU2 sig=0x306c3, pf=0x10, revision=0x1f
[    2.276152] microcode: CPU3 sig=0x306c3, pf=0x10, revision=0x1f
[    2.276621] microcode: CPU4 sig=0x306c3, pf=0x10, revision=0x1f
[    2.276890] microcode: CPU5 sig=0x306c3, pf=0x10, revision=0x1f
[    2.277148] microcode: CPU6 sig=0x306c3, pf=0x10, revision=0x1f
[    2.277404] microcode: CPU7 sig=0x306c3, pf=0x10, revision=0x1f
[    2.277670] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

[/COLOR]


```[/FONT]
This is what I get after downloading the last microcode from Intel's website and extracting it to /tmp/micro. The signature seems to be OK, but I do not understand how "[FONT=lucida console]pf[/FONT]" and "[FONT=lucida console]revision[/FONT]" work.

---

### Post by Linuxisfast on 2016-05-15
Yes in latest Ubuntu 16.04 its installed automatically. I am just curious and if you have time on hand, would you just run latest 14.04 from live CD and measure your CPU frequency if possible.

---

### Post by Linuxisfast on 2016-05-15
[http://imgur.com/ZK1GEWs](http://imgur.com/ZK1GEWs) intel Haswell under Arch, notice all cores at turbo with high voltage.

---

### Post by Aquignis on 2016-05-16
All your cores are around 3.5 GHz to 4 GHz but in C7 state most of the time, so I think that you're not consuming too much power and we can see that you have good temperatures. Of course 800 MHz would be better...
In my case, I both have high frequencies and my first core spending much time working for nothing in C0. And the second one seems to be hesitating...

On the live CD with 14.04 I get [this monitoring results]("http://imgur.com/Ctn4JZI") with [this analysis of my CPU]("http://pastebin.com/H0QB84j4"). We can notice that i7z detects my processor as a member of the Nehalem family. This problem does not appear in the previous execution of i7z.

---

### Post by Linuxisfast on 2016-05-16
You have some serious issues of runaway process here. My temps on Arch are high and so is power consumption due to high frequency at idle.

---

### Post by Aquignis on 2016-05-16
Yep. Unfortunately, identify the process and eliminate it is beyond the scope of my skills...

---

### Post by Linuxisfast on 2016-05-16
> **Aquignis said:**
> Yep. Unfortunately, identify the process and eliminate it is beyond the scope of my skills...


Can you run powertop?

---

### Post by Aquignis on 2016-05-16
The results are the following:
- what stays in the terminal after running PowerTOP: [http://pastebin.com/N5BNkd92](http://pastebin.com/N5BNkd92)
- overview: [http://pastebin.com/625h2tvD](http://pastebin.com/625h2tvD)
- other stats: [http://imgur.com/a/x4tA4](http://imgur.com/a/x4tA4)
If you drive crazy with the resolution of the screenshots, let me know, I will try to do better. I suggest that you download the pictures, Imgur does not allow to zoom in enough.

---

### Post by Linuxisfast on 2016-05-17
Thanks, can you install linux-power-tools that brings Turbostat. After that just post the command in terminal and we get to see the errant CPU processes if any thats causing all this heat. [http://manpages.ubuntu.com/manpages/xenial/man8/turbostat.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/turbostat.8.html)

---

### Post by Aquignis on 2016-05-19
Please find attached a text file with the results of turbostat. I have added some additional information that comes from the --debug option. The file has a quite high width !

---

### Post by Linuxisfast on 2016-05-19
> **Aquignis said:**
> Please find attached a text file with the results of turbostat. I have added some additional information that comes from the --debug option. The file has a quite high width !


In case you noticed your average MHz looks fine, same as mine. However your temp issue needs to be looked into.

---

### Post by Linuxisfast on 2016-05-19
[https://github.com/leoluk/thinkpad-stuff/wiki/Haswell-ThinkPad-problems](https://github.com/leoluk/thinkpad-stuff/wiki/Haswell-ThinkPad-problems) take a look here, some interesting issues also concerning Linux. Also this [https://forums.gentoo.org/viewtopic-t-986976-start-0.html](https://forums.gentoo.org/viewtopic-t-986976-start-0.html) and this [https://bugzilla.redhat.com/show_bug.cgi?id=859597](https://bugzilla.redhat.com/show_bug.cgi?id=859597)

---

### Post by Aquignis on 2016-05-19
Yes, it surprised as the other tools we have used do not display this statistic. Are we sure that having a normal average frequency means that the behaviour of the CPU is normal ? There is one thing I'm sure of, because I tested it: when I set the  CPU to 800 MHz, there is no heat or energy consumption problem anymore. That is why I'm a little bit lost here...

If it is not the CPU, what could it be ? The fan is spinning fast and is noisy compared to Windows, so heat dissipation is probably normal. Moreover, I think that the GPU is disabled.

---

### Post by Linuxisfast on 2016-05-19
> **Aquignis said:**
> Yes, it surprised as the other tools we have used do not display this statistic. Are we sure that having a normal average frequency means that the behaviour of the CPU is normal ? There is one thing I'm sure of, because I tested it: when I set the  CPU to 800 MHz, there is no heat or energy consumption problem anymore. That is why I'm a little bit lost here...

If it is not the CPU, what could it be ? The fan is spinning fast and is noisy compared to Windows, so heat dissipation is probably normal. Moreover, I think that the GPU is disabled.

Windows runs something equivalent of cpu-freq unlike intel_pstate, if that runs your CPU cooler, no harm in running it like that.

---

### Post by Aquignis on 2016-05-19
I have already tried it before via an option in the kernel: "intel_pstate=disable". It improves the situation, but does not solve the problem (still 4 hours of battery life):
```

    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
       -       -     272   14.34    1900    2494       0   35.77    0.06    0.03   49.80      62      62    0.00    0.00    0.00    0.00   10.80    3.33    0.05
       0       0    1360   71.71    1900    2494       0   28.29    0.00    0.00    0.00      62      62    0.00    0.00    0.00    0.00   10.80    3.33    0.05
       0       1       9    0.48    1899    2494       0   99.52
       1       2       3    0.17    1904    2494       0   99.79    0.04    0.00    0.00      54
       1       3     798   42.10    1900    2494       0   57.86
       2       4       2    0.10    1873    2494       0    0.19    0.16    0.12   99.43      50
       2       5       0    0.02    1914    2494       0    0.27
       3       6       3    0.14    1889    2494       0    0.05    0.03    0.00   99.78      43
       3       7       0    0.02    1910    2494       0    0.17
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
       -       -     271   14.32    1900    2494       0   35.77    0.01    0.00   49.91      62      62    0.00    0.00    0.00    0.00   10.78    3.32    0.05
       0       0    1353   71.39    1900    2494       0   28.61    0.00    0.00    0.00      62      62    0.00    0.00    0.00    0.00   10.78    3.32    0.05
       0       1       9    0.46    1900    2494       0   99.54
       1       2      41    2.16    1900    2494       0   97.84    0.00    0.00    0.00      54
       1       3     763   40.26    1900    2494       0   59.74
       2       4       2    0.10    1900    2494       0    0.08    0.02    0.00   99.80      49
       2       5       1    0.03    1900    2494       0    0.15
       3       6       2    0.10    1900    2494       0    0.05    0.01    0.00   99.85      42
       3       7       0    0.02    1901    2494       0    0.13

```

---

### Post by Linuxisfast on 2016-05-19
> **Aquignis said:**
> I have already tried it before via an option in the kernel: "intel_pstate=disable". It improves the situation, but does not solve the problem (still 4 hours of battery life):
```

    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
       -       -     272   14.34    1900    2494       0   35.77    0.06    0.03   49.80      62      62    0.00    0.00    0.00    0.00   10.80    3.33    0.05
       0       0    1360   71.71    1900    2494       0   28.29    0.00    0.00    0.00      62      62    0.00    0.00    0.00    0.00   10.80    3.33    0.05
       0       1       9    0.48    1899    2494       0   99.52
       1       2       3    0.17    1904    2494       0   99.79    0.04    0.00    0.00      54
       1       3     798   42.10    1900    2494       0   57.86
       2       4       2    0.10    1873    2494       0    0.19    0.16    0.12   99.43      50
       2       5       0    0.02    1914    2494       0    0.27
       3       6       3    0.14    1889    2494       0    0.05    0.03    0.00   99.78      43
       3       7       0    0.02    1910    2494       0    0.17
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
       -       -     271   14.32    1900    2494       0   35.77    0.01    0.00   49.91      62      62    0.00    0.00    0.00    0.00   10.78    3.32    0.05
       0       0    1353   71.39    1900    2494       0   28.61    0.00    0.00    0.00      62      62    0.00    0.00    0.00    0.00   10.78    3.32    0.05
       0       1       9    0.46    1900    2494       0   99.54
       1       2      41    2.16    1900    2494       0   97.84    0.00    0.00    0.00      54
       1       3     763   40.26    1900    2494       0   59.74
       2       4       2    0.10    1900    2494       0    0.08    0.02    0.00   99.80      49
       2       5       1    0.03    1900    2494       0    0.15
       3       6       2    0.10    1900    2494       0    0.05    0.01    0.00   99.85      42
       3       7       0    0.02    1901    2494       0    0.13

```


So you use nvidia-prime to shut down GPU? btw whats your GFX Watt consumption? In case Intel is on, that will be indicated.

---

### Post by Aquignis on 2016-05-19
I was using bbswitch. I just tried prime via nvidia-settings and general power consumption is the same (25 W instead of 24 W, monitored with PowerTOP and after I chose tu use Intel integrated graphics only).

>  btw whats your GFX Watt consumption? 
How can I monitor the specific power consumption  of my NVIDIA card ? PowerTOP shows me in "Device stats":
```
0.0% PCI Device: NVIDIA Corporation Ethernet GK208M [GeForce GT 730M]
```
And the sum on all devices of "Usage" percentages is over 100 %...

---

### Post by Linuxisfast on 2016-05-19
> **Aquignis said:**
> I was using bbswitch. I just tried prime via nvidia-settings and general power consumption is the same (25 W instead of 24 W, monitored with PowerTOP and after I chose tu use Intel integrated graphics only).


How can I monitor the specific power consumption  of my NVIDIA card ? PowerTOP shows me in "Device stats":
```
0.0% PCI Device: NVIDIA Corporation Ethernet GK208M [GeForce GT 730M]
```
And the sum on all devices of "Usage" percentages is over 100 %...


Nope I meant GFX consumption of your intel, in case its Nvidia, that means its not switched off.

---

### Post by mc4man on 2016-05-19
I'd think something very local to your hardware or setup or thinkpad 540 in general.
Here have very similar hardware though a lenovo ideapad

Basic's after up a couple of hrs of various activities, so cpu stressful, ambient temp around 70. 

> doug@doug-Lenovo-IdeaPad-Y510P:~$ inxi -b
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.4.0-22-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO product: 20217 v: Lenovo IdeaPad Y510P
           Mobo: LENOVO model: VIQY0Y1 v: 31900058STD Bios: LENOVO v: 74CN44WW(V3.05) date: 09/18/2013
CPU:       Quad core Intel Core i7-4700MQ (-HT-MCP-) speed/max: 2399/3400 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@59.91hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Qualcomm Atheros QCA8171 Gigabit Ethernet driver: alx
           Card-2: Intel Wireless 7260 driver: iwlwifi
Drives:    HDD Total Size: 524.1GB (15.3% used)
Info:      Processes: 251 Uptime: 2:09 Memory: 900.1/7895.8MB Client: Shell (bash) inxi: 2.2.35 

```
doug@doug-Lenovo-IdeaPad-Y510P:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate

doug@doug-Lenovo-IdeaPad-Y510P:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave


doug@doug-Lenovo-IdeaPad-Y510P:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
826406
800250
799968
800156
800062
800531
809531
845906

doug@doug-Lenovo-IdeaPad-Y510P:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
1325437
856968
800718
1463437
1015218
891000
1600031
1383281

doug@doug-Lenovo-IdeaPad-Y510P:~$ grep MHz /proc/cpuinfo 
cpu MHz		: 897.656
cpu MHz		: 802.312
cpu MHz		: 1099.968
cpu MHz		: 881.437
cpu MHz		: 1100.062
cpu MHz		: 799.968
cpu MHz		: 852.281
cpu MHz		: 839.343

doug@doug-Lenovo-IdeaPad-Y510P:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:            N/A  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +44.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:         +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:         +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:         +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:         +40.0°C  (high = +84.0°C, crit = +100.0°C)

doug@doug-Lenovo-IdeaPad-Y510P:~$ cat /sys/devices/system/cpu/intel_pstate/min_perf_pct 
23
```

---

### Post by Linuxisfast on 2016-05-19
mc4man nails it........I still suspect that the video card is not shut off. Do a fresh install of 16.04, then the video driver via driver applet. After the reboot, turn it off via nvidia-settings and then re login. Also make sure to install TLP, report back.

However the new Haswells run at far higher frequency even on idle due to pstate bug thats been discussed over Arch forum and bugzilla so even my desktop Haswell runs at far higher frequencies compared to my Sandybridge i5 in x220.

---

### Post by Doug S on 2016-05-20
> **Linuxisfast said:**
> However the new Haswells run at far higher frequency even on idle due to pstate bug thats been discussed over Arch forum and bugzilla so even my desktop Haswell runs at far higher frequencies compared to my Sandybridge i5 in x220.I believe that issue will be (mostly) solved as of kernel 4.6.

References:
[https://bugzilla.kernel.org/show_bug.cgi?id=115771]("https://bugzilla.kernel.org/show_bug.cgi?id=115771")
[https://bugzilla.kernel.org/show_bug.cgi?id=93521]("https://bugzilla.kernel.org/show_bug.cgi?id=93521")
[https://lkml.org/lkml/2016/3/29/692]("https://lkml.org/lkml/2016/3/29/692") (which eventually became bug 115771)

---

### Post by Linuxisfast on 2016-05-20
> **Doug S said:**
> I believe that issue will be (mostly) solved as of kernel 4.6.

References:
[https://bugzilla.kernel.org/show_bug.cgi?id=115771](https://bugzilla.kernel.org/show_bug.cgi?id=115771)
[https://bugzilla.kernel.org/show_bug.cgi?id=93521](https://bugzilla.kernel.org/show_bug.cgi?id=93521)
[https://lkml.org/lkml/2016/3/29/692](https://lkml.org/lkml/2016/3/29/692) (which eventually became bug 115771)


Tried 4.6 from Arch testing, not much difference. Btw Ubuntu 16.04 kernel's frequency for Haswell refresh is now quite close to Arch so yes, your point about Red herring for 300MHz was correct.

---

### Post by mc4man on 2016-05-20
> **Linuxisfast said:**
> 
However the new Haswells run at far higher frequency even on idle due to pstate bug thats been discussed over Arch forum and bugzilla 
I really don't see that here. I've 3 laptops - sandybridge, haswell & skylake. The skylake is a crappy i7 6500u so not relevant. (speed/max: 499/3100 MHz)
As far as the other 2, both i7, I'd say at idle the haswell goes lower than the sandybridge though both scale well & run cool. The only real diff atm is the sandybridge is on 14.04.4/4.2 kernel & the haswell is 16.04/4.4 kernel. I'll likely move the sandybridge back to 14.04.1 to get away from the broken/no added value  mesa 11

---

### Post by Linuxisfast on 2016-05-21
> **mc4man said:**
> I really don't see that here. I've 3 laptops - sandybridge, haswell & skylake. The skylake is a crappy i7 6500u so not relevant. (speed/max: 499/3100 MHz)
As far as the other 2, both i7, I'd say at idle the haswell goes lower than the sandybridge though both scale well & run cool. The only real diff atm is the sandybridge is on 14.04.4/4.2 kernel & the haswell is 16.04/4.4 kernel. I'll likely move the sandybridge back to 14.04.1 to get away from the broken/no added value  mesa 11


Are your Haswell the refresh editions? Only 4790 and its K edition suffers from this, not the others.

---

### Post by Linuxisfast on 2016-05-21
[http://www.phoronix.com/scan.php?page=article&item=linux-47-schedutil&num=5](http://www.phoronix.com/scan.php?page=article&item=linux-47-schedutil&num=5)


In early days of intel_pstate Coling King and Canonical disabled it in initial release of Ubuntu 12.04LTS and only in later HWE it was enabled. With Haswell refresh CPUs its been story of CPU running at full frequency constantly even at idle leading to increased power consumption and heat. I guess its time to bring CPUFREQ back in light of these results. Time and again its shown no different in performance as it had promised over the trusted cpufreq.

---

### Post by Doug S on 2016-05-21
> **Linuxisfast said:**
> [http://www.phoronix.com/scan.php?page=article&item=linux-47-schedutil&num=5](http://www.phoronix.com/scan.php?page=article&item=linux-47-schedutil&num=5)Thanks for the link.
Those test results do not make any sense to me. I added a comment with some of my test results.

---

### Post by Linuxisfast on 2016-05-21
> **Doug S said:**
> Thanks for the link.
Those test results do not make any sense to me. I added a comment with some of my test results.


I saw that but pstate is not showing its advantage over cpufreq in true sense, am sure you would agree.

---

### Post by Linuxisfast on 2016-05-25
> **Doug S said:**
> Thanks for the link.
Those test results do not make any sense to me. I added a comment with some of my test results.


Some new development.  [https://www.phoronix.com/scan.php?page=news_item&px=P-State-Possible-4.6-Regression](https://www.phoronix.com/scan.php?page=news_item&px=P-State-Possible-4.6-Regression)

---

