---
title: "Laptop running really hot"
date: 2015-01-05
forum: Hardware
---

### Post by dorlow on 2015-01-05
My laptop is running extremely hot with Ubuntu 14.04.  I've already implemented the PSTATE fix for my Intel processor and it's still running hot enough.  And then sometimes freezes and I have to hard power it off.  Does anyone have any other ideas to get it to run cooler?  Running Linux, the case where my wrists rest is hot.  If I was running Windows, it would be cool.

---

### Post by Doug S on 2015-01-05
> **dorlow said:**
> I've already implemented the PSTATE fix for my Intel processor and it's still running hot enough. What do you mean by PSTATE fix? Do you mean you are using the intel_pstate frequency governor driver?
Are you also using thermald? (to check: dpkg -l |grep thermald) If yes, try with it disabled or removed.

---

### Post by A_good_user on 2015-01-05
Could you please install lm-sensors and tell us how high temps are?

```

sudo apt-get install lm-sensors
```

---

### Post by dorlow on 2015-01-06
Just installed psensor

temp1 99 C
temp2 30 C
Physcal ID 0 100 C
Core 0 100C
Core 1 98 C
Core 2 97 C

My laptop is hot enough it's burning my hands.  The fans are running constantly.

---

### Post by dorlow on 2015-01-06
> **Doug S said:**
> What do you mean by PSTATE fix? Do you mean you are using the intel_pstate frequency governor driver?
Are you also using thermald? (to check: dpkg -l |grep thermald) If yes, try with it disabled or removed.

edit /etc/default/grub

Added to the end of the line intel_pstate=enable

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=enable"

to the line that says...

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Also I tried the dpkg -l | grep thermald and I didn't get any return, so it's not installed.

---

### Post by dorlow on 2015-01-06
Here's some other good info...

david@david-laptop:~$ cpupower frequency-info
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 1.20 GHz - 3.30 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 1.20 GHz and 3.30 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.21 GHz.
  boost state support:
    Supported: yes
    Active: yes
    25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores

So, it appears my processors are running at 50% the max speed.  So why so hot?

---

### Post by Yellow Pasque on 2015-01-07
Is this a laptop with hybrid/switchable graphics?
```
lspci
```

It might help if you told us what model of laptop you had. Do you call your mechanic and not tell him/her what kind of car you have?

---

### Post by dorlow on 2015-01-07
Well, I changed my mode to powersave and the laptop is running about 20 degrees cooler than yesterday.  But in Windows, I can run it at full speed without having to worry about heat issues.

---

### Post by dorlow on 2015-01-07
Here's the output of lspci...

david@david-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0a:00.0 Network controller: Ralink corp. Device 539a
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
david@david-laptop:~$ 


I have an HP Pavilion DV6 laptop.

---

### Post by Yellow Pasque on 2015-01-07
Yeah, it's an Optimus/hybrid graphics system. I bet the nvidia GPU is what's heating up the system. In the "old" days, the solution would be to install bumblebee, but primus is supposed to be working out of the box in Ubuntu 14.04. I'm not sure what the solution is nowadays, but Optimus systems are pretty common, so someone should know how to tackle it. Good luck.

```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M]
```

---

### Post by Doug S on 2015-01-07
> **dorlow said:**
> Well, I changed my mode to powersave and the laptop is running about 20 degrees cooler than yesterday.With the intel_pstate driver there is only powersave and performance modes, so I do not understand the statement. You must have been in powersave mode already, or your output from "cpupower frequency-info" would have been different.

Edit: Oh, I see that it was in performance mode before. I missed that earlier```
current policy: frequency should be within 1.20 GHz and 3.30 GHz.
                  The governor "[COLOR=#ff0000]performance"[/COLOR] may decide which speed to use
                  within this range.
  [COLOR=#ff0000]current CPU frequency is 1.21 GHz.[/COLOR]
  boost state support:
    Supported: yes
    Active: yes
    [COLOR=#ff0000]25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores[/COLOR]

So, it appears my processors are running at 50% the max speed.  So why so hot?
```No, your CPU clock was pretty much minimum, at 1.21 GHz.
Your max turbo lines do not make sense. They are typically different for each line. Example (output from turbostat):```
35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores
```

---

### Post by Yellow Pasque on 2015-01-08
^Good call. I wonder if trying the latest upstream kernel might show better results?

---

### Post by Doug S on 2015-01-08
> **Temüjin said:**
> ^Good call. I wonder if trying the latest upstream kernel might show better results?yes, the poster should try kernel 3.19RC3 (which is the current release candidate, or whatever version if there is significant delay until the test).
See:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc3-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc3-vivid/) (and don't worry that is says "vivid" it will work on trusty, or at least it should)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

By the way, I agree, and also think the heat source is the GPU. Use turbostat to get more information. Example(s):```
doug@s15:~/temp$ [COLOR=#ff0000]sudo ./turbostat -S sleep 20[/COLOR]
Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
     809   38.88    2082    3411       0   23.57    0.92   36.64    0.00      45      45    0.06    0.36    0.64    0.00   18.11   14.11    [COLOR=#ff0000]0.23[/COLOR]
20.001285 sec
doug@s15:~/temp$ [COLOR=#ff0000]sudo ./turbostat -S -J sleep 20[/COLOR]
Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7   Pkg_J   Cor_J   GFX_J   time
     817   38.67    2112    3412       0   24.34    1.16   35.83    0.00      44      44    0.06    0.34    0.58    0.00  368.79  288.52    [COLOR=#ff0000]4.68[/COLOR]   20.00
20.001318 sec
doug@s15:~/temp$
```

---

