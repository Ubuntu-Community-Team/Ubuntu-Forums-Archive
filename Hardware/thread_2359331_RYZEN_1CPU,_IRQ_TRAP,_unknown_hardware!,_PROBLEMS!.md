---
title: "RYZEN 1CPU, IRQ TRAP, unknown hardware!, PROBLEMS!!!"
date: 2017-04-22
forum: Hardware
---

### Post by TheOmegaMan on 2017-04-22
It has been almost 2 months that AMD Ryzen has been released and there does not seem to be any fix for this. Tell me what you need from me to provide to you to get it this fixed.

The errors:

-core perfctr but no constraints; unknown hardware!
-Unexpected irq trap at vector 7
-Only detecting 1 core if the system actually boots up

The hardware in question:
Gigabyte AX370-Gaming 5 F5 BIOS (but it appears that all gigabyte chipsets are affect, at least the majority of chipsets mentioned with errors above are gigabyte motherboards)

What is weird:
-Ubuntu 16.04.1 works (although it gives the error core; perfctr but no constraints; unknown hardware!), all cores are detected and no IRQ trap error.
-Updating 16.04.1 kernels to any of the 4.4 kernels doesn't break anything, updating to any other later kernel does (4.8 or 4.10)
-Ubuntu 16.04.2, 16.10, 17.04 do not work

What I have been able to test with results:
-If IRQ trap at vector 7 errors occur you will not be able to boot.
-If I disable legacy USB in BIOS makes the IRQ trap error go away but only one core detected.
-If I set kernel option acpi=off IRQ trap error goes away, but only one core detected
-The mic does not appear to work and sound card has crackle/hiss and has delayed playback, 4.11 kernel is supposed to have the proper ACL1220 codec driver to support the sound.
-If I install mainline 4.11 kernel on any of the versions mentioned above I get all the errors and if I set acpi=off it only detects 1 core.

```
/$ uname -a
Linux ###### 4.4.0-75-generic #96-Ubuntu SMP Thu Apr 20 09:56:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
/$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                16
On-line CPU(s) list:   0-15
Thread(s) per core:    2
Core(s) per socket:    8
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            23
Model:                 1
Model name:            AMD Ryzen 7 1700X Eight-Core Processor
Stepping:              1
CPU MHz:               3400.000
CPU max MHz:           3400.0000
CPU min MHz:           2200.0000
BogoMIPS:              6786.96
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             64K
L2 cache:              512K
L3 cache:              8192K
NUMA node0 CPU(s):     0-15
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 clzero arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
```

Now on 4.10 kernel:

```
/$ uname -a
Linux ###### 4.10.0-20-generic #22~16.04.1-Ubuntu SMP Thu Apr 20 17:43:29 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
/$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            23
Model:                 1
Model name:            AMD Ryzen 7 1700X Eight-Core Processor
Stepping:              1
CPU MHz:               3393.288
BogoMIPS:              6786.57
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             64K
L2 cache:              512K
L3 cache:              8192K
NUMA node0 CPU(s):     0
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
```

Tell me what you need extra to help in TS this problem. Don't know why only 16.04.1 works (I will admit I have not tried 16.04) but the rest don't. Pretty much any other distro doesn't seem to have the problem only Ubuntu and its derivatives (I have tried Ubuntu Gnome, MATE, Kubuntu, Budgie-Remix, Ubuntu Budgie). Other distros I have tried where I don't have the problem is, Fedora, Manjaro, Antergos, Solus Project.

---

### Post by tr262 on 2017-04-23
[FONT=arial]I have the exact same problems with a Ryzen 1500X and a Gigabyte GA-AB350M-HD3 Motherboard. However, with kernel 4.4.63-04063-generic from mainline, the system boots fine with the only error message being:
```
 [       0.354383] core perfctr but no constraints; unknown hardware!
```
[/FONT]

---

### Post by pete-br on 2017-04-24
I also have a Motherboard with X370 chipset. My cpu is a  AMD Ryzen 5 1600X.

I chose to install Ubuntu 17.04 onto it because it's faster to keep up-to-date with the newest software, drivers and kernel.
During installation I checked the boxes to allow the download of updates and of proprietary drivers.
After the installation completed I went to the software center and let it check for updates.
It found a proprietary driver for my AMD CPU which I then selected to be installed.

I don't have problems with perfctr or 'unknown hardware'. 
I don't know if my installation had problems before I let it check for updates.
But maybe this information can be of help.

---

### Post by TheOmegaMan on 2017-04-24
Thank you tr262 and pete-br the more we add to help Canonical the quicker (hopefully) it get resolved. 

From the gigabyte [forum]("http://forum.gigabyte.us/thread/886/am4-beta-bios-thread?page=40"):

"Yes, it is "fixed" upstream, by that I mean, disabled.

Enabling CONFIG_PINCTRL_AMD will just do nothing on a gigabyte board. Ubuntu should not have enabled that and it's probably not a BIOS issue but more about GPIO wired in the NB that gigabyte BIOS use to control some aspect on the board.

They are GPIO pin linked to stuff, without the board schematics, can't really say what but it could be for example the way gigabyte use to control the leds light show from the firmware.

CONFIG_PINCTRL_AMD probably try to take over the control of these GPIO pin with create a conflict with the NB.

Installing/using GPIO driver on desktop board is pointless, they never have GPIO pin exposed for the user anyway. Others distribs just don't enable everything not related to anything useful in the kernel."


Not sure if this helps but a user on that forum appears to have the answer, I have not had a chance to recompile my kernel yet to see if this actually does fix it or not. If I have time tonight I will check it out... don't just have problems with the PC but my car needs some TLC as well and daylight is dissipating. Will report back.

---

### Post by TheOmegaMan on 2017-04-25
I fixed the problem, it only cost me an extra 271 dollars. I bought a new motherboard... Gigabyte didn't seem to be in a hurry and I can't blame Ubuntu since only one AM4 vendor out of the 5 out there seem to be having the problem (gigabyte). I bought a MSI Gaming Pro Carbon... now on 17.04 all cores not unexpected irq trap at vector 7.

Kinda really disappointed in Gigabyte... it will be a while before I spend any of my money on them again. Although I do like a few of the features they have and their BIOS is much more functional than MSI's I can say I am happy to be able to use any and all versions of currently supported Ubuntu... Found an XDA developer article that says that Gigabyte boards also have issues with SuSE so it isn't just Ubuntu. At any rate the MSI board was the one I wanted to begin with but some dumbass at the computer store convinced me that Gigabyte is the best in the universe... I guess he is an Intel fanboy and thinks chipsets are the same between two architectures. He even tried to defend Gigabyte even though I had pointed him to the XDA article that specifically says it is a Gigabyte problem and also specifically says that other vendors are not affected by this. I guess fanboi's be fanboi's, I used to be ontop of these things about half a dozen years ago but since then I bought my first house, then a care then had a son and then a daughter and then bought a second fix me upper house so I have been very busy and don't have the time I used to, to look into these things. I clearly remember 25 years ago when I started in computers I thought that by now the "young'ns" would be pwning me in knowledge and understanding but I guess I was wrong.

Ah well, still debating if I should sell the Gigabyte board or be patient and wait for Gigabyte to fix  and build a second system... I have been wanting to upgrade my NAS/VM'ing server.

XDA article I was talking about: [https://www.xda-developers.com/xda-takes-on-ryzen-in-depth-look-of-amds-new-processors-on-the-linux-side/](https://www.xda-developers.com/xda-takes-on-ryzen-in-depth-look-of-amds-new-processors-on-the-linux-side/)

---

### Post by P-I H on 2017-04-26
I have a MSI Tomahawk B350 motherboard. It works OK, but there is a problem with sensors. It might be the same problem with [COLOR=#000000]MSI Gaming Pro Carbon...[/COLOR]
There is information on this site
[https://github.com/groeck/nct6775/issues/49](https://github.com/groeck/nct6775/issues/49)

I have done the following to fix the problem.
I have created the the file **/etc/rc.local** with the following content:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe nct6775 force_id=0xd120
exit 0


and changed permission to allow executing of /etc/rc.local as a program



[COLOR=#000000]
[/COLOR]

---

### Post by tr262 on 2017-04-29
Using the modified kernel, everything works fine.
The kernel can be found here:
[http://www.nextized.net/repo/linux/ubuntu-linux-4.10.3_ryzen01_amd64_generic.tar.gz](http://www.nextized.net/repo/linux/ubuntu-linux-4.10.3_ryzen01_amd64_generic.tar.gz)

---

### Post by peter-ludwig on 2017-06-06
I have the AMD Ryzen 1700 on a Gigabyte AX370-Gaming K5 with BIOS: 4.4.0-77-generic and I too got this message. (But even with the orig. Kernel it was running ok. I upgraded because of the sensors problem - which did not help)
I am running Mint Mate 18.1
My CPUs are all running fine too and I do not have any problems apart from the following:

My sensors (any temperature sensor) were not reported at all.
Conky Seamod Theme does not run correctly. The CPU dials are not shown. (But this can wait)

@tr262
Out of curiosity I tried to modprobe nct6775 - but that did not work. (no such device)

I then tried:
```
sudo sensors-detect
```

which reported:
```
Trying family `ITE'... Yes
```
```
Found unknown chip with ID 0x8686
```
```
Found unknown chip with ID 0x8733
```
```
Found unknown SMBus adapter 1022:790b at 0000:00:14.0.
```

I then found this thread:

[http://github.com/groeck/it87/issues/16](http://github.com/groeck/it87/issues/16)

and this one:

[https://askubuntu.com/questions/748615/lm-sensors-not-returning-cpu-temp-it87](https://askubuntu.com/questions/748615/lm-sensors-not-returning-cpu-temp-it87)

I loaded:

```
sudo modprobe it87
```

and then 

```
sensors
```

reported:

> 
it8686-isa-0a40
Adapter: ISA adapter
in0:          +0.85 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.03 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.03 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +0.88 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +0.89 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.29 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.02 V  
fan1:        1032 RPM  (min =    0 RPM)
fan2:         968 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +46.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +22.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = AMD AMDSI
temp4:        +34.0°C  (low  = +127.0°C, high = +127.0°C)
temp5:        +39.0°C  (low  =  +0.0°C, high = -114.0°C)  sensor = thermistor
temp6:        +38.0°C  (low  =  +0.0°C, high = -114.0°C)
intrusion0:  ALARM

it8792-isa-0a60
Adapter: ISA adapter
in0:          +0.39 V  (min =  +0.00 V, max =  +2.78 V)
in1:          +0.88 V  (min =  +0.00 V, max =  +2.78 V)
in2:          +1.05 V  (min =  +0.00 V, max =  +2.78 V)
+3.3V:        +3.36 V  (min =  +0.00 V, max =  +5.56 V)
in4:          +1.29 V  (min =  +0.00 V, max =  +2.78 V)
in5:          +1.16 V  (min =  +0.00 V, max =  +2.78 V)
in6:          +2.78 V  (min =  +0.00 V, max =  +2.78 V)  ALARM
3VSB:         +3.36 V  (min =  +0.00 V, max =  +5.56 V)
Vbat:         +3.05 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM


Others seem to have GPU sensors too? (amdgpu-pci-0c00) ????


**Then I installed:**

```
sudo apt install xsensors
```

to have a nice GUI.

Then running 

```
xsensors
```

Makes it look like this: (This pic is borrowed from:
[https://askubuntu.com/questions/748615/lm-sensors-not-returning-cpu-temp-it87](https://askubuntu.com/questions/748615/lm-sensors-not-returning-cpu-temp-it87)

[IMG]https://i.stack.imgur.com/rnKXV.png[/IMG]

This pic does not show my sensors but is similar. Thanks to the girl/guy who uploaded it.

**I added** ```
it87
``` into /etc/modules to make it load during boot.

Thanks for infos!

---

