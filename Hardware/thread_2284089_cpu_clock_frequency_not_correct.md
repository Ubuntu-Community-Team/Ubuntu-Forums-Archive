---
title: "cpu clock frequency not correct"
date: 2015-06-27
forum: Hardware
---

### Post by ryan166 on 2015-06-27
Hi guys, have a friends  laptop who complained of it being very slow. so decided to wipe it clean and run ubuntu.

Its a turion x2 RM-77 dual core 2.3ghz.

however when i do cpuinfo, hwinfo and lscpu they all show clock speed as 575mhz. have put  alot of load ont he cpu but it doesnt budge and it is still indeed slow with over 100% cpu load when openign web browsers etc. 

anyway to fix this, mirco code version is 0x20000057

temps are all good, under 50 degrees!

---

### Post by QIII on 2015-06-27
Hello!

Does the BIOS have any settings for CPU throttling?  Check through the settings carefully.  The BIOS may have a setting to allow the CPU frequency to rise with demand.

---

### Post by ryan166 on 2015-06-27
> **QIII said:**
> Hello!

Does the BIOS have any settings for CPU throttling?  Check through the settings carefully.  The BIOS may have a setting to allow the CPU frequency to rise with demand.

Thats a good quesiton, this is a toshiba laptop, and the cpu seems to be locked down, the bios has absolutely no settings in there, nothing for cpu at all. However it does show on the main screen in bios cpu frequency = 2300mhz. Seems to be once OS has loaded the cpu stepping is broken!

---

### Post by QIII on 2015-06-27
Let's see for sure what is going on.

Open a terminal and issue the following command, which will report the operating speed of the CPU in 1 second increments.

```
watch -n 1 grep Hz /proc/cpuinfo
```

Watch what happens to the clock speeds of the cores as you increase and decrease the load on your CPU.

---

### Post by ryan166 on 2015-06-27
Okay tried leaving that running for 15 minutes while loading up apps and multitasking. 2x cores both showing 575.00 and didn't budge once!

---

### Post by QIII on 2015-06-27
What is the model of the machine?

We might be able to find some tech specs to help.

It has been a long time since I have used any CPU frequency management tools with Linux, primarily because that is either handled by BIOS settings and a module in the kernel.

By the way, it occurs to me that some OEMs may list the BIOS setting as something similar to "Power Save",

---

### Post by ryan166 on 2015-06-27
Its a Toshiba L500d. Even power options are not in bios haha all I can do is set the clock set the HDD mode and choose boot order literally that's it's!!

---

### Post by ryan166 on 2015-06-27
does this look correct??

```
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.00 ms.
  hardware limits: 575 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 1.15 GHz, 575 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 575 MHz and 575 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 575 MHz.
  cpufreq stats: 2.30 GHz:0.00%, 1.15 GHz:0.00%, 575 MHz:100.00%  (1)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 0.00 ms.
  hardware limits: 575 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 1.15 GHz, 575 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 575 MHz and 575 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 575 MHz.
  cpufreq stats: 2.30 GHz:0.00%, 1.15 GHz:0.00%, 575 MHz:100.00%  (1)
```

---

### Post by Yellow Pasque on 2015-06-27
No, this part is not correct:
```
frequency should be within 575 MHz and 575 MHz
```

Try setting it manually and check again:
```
sudo cpufreq-set -u 2300
cpufreq-info
```

---

### Post by Doug S on 2015-06-27
Also, what do you get for this?:```
cat /sys/devices/system/cpu/cpu0/cpufreq/bios_limit
```

---

### Post by ryan166 on 2015-06-27
found the issue finally!! so the bios is telling the OS to limit the cpu because either the charger or the battery are not official oem products. So I can bypass that by:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.ignore_ppc=1"
then update grub now cpu reports correctly!!

thanks for help guys. was tricky to torubleshoot because the os sees the cpu correctly and its capabilities, but what is tricky tot see is the bios sending that flag to the os not to run higher than the lowest frequency! glad its all fixed now.

---

