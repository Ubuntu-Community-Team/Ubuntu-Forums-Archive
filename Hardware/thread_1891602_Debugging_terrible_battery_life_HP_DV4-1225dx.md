---
title: "Debugging terrible battery life HP DV4-1225dx"
date: 2011-12-06
forum: Hardware
---

### Post by deadguy on 2011-12-06
Hi all,

I'm looking for advice to improve the terrible battery life on my HP DV4-1225dx.  I'm running an up to date 11.10.

There are a few problems with it: 
1) The battery only lasts about an hour on a full charge.  
2) Any time I unplug it, ubuntu thinks it's about to run out of battery and hibernates (once it wake it back up, it doesn't complain for ~ an hour).  
3) When unplugged, the `present rate` from /proc/acpi/battery/BAT0/state is always 0mA.
4) Powertop doesn't appear to be working.  The summary line (even after leaving it running for a few hours) is always: 

```
Summary: 0.0 wakeups/second,  0.0 GPU ops/second and 0.0 VFS ops/sec
```

I've searched all over, but haven't gotten anywhere.  Any advice will be greatly appreciated!

Here are the facts:

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

```

$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         4400 mAh
last full capacity:      3262 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 164 mAh
design capacity low:     98 mAh
cycle count:		  0
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            Primary
serial number:           
battery type:            Lion
OEM info:                Hewlett-Packard

```


```

$ cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      3262 mAh
present voltage:         12518 mV

```

```

$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 525 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz.
  cpufreq stats: 2.10 GHz:32.00%, 1.05 GHz:2.49%, 525 MHz:65.51%  (1939136)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 525 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz.
  cpufreq stats: 2.10 GHz:15.26%, 1.05 GHz:1.44%, 525 MHz:83.31%  (42791)

```

---

### Post by phidia on 2011-12-06
There is a somewhat painful explanation about the general state of laptop battery efficiency [here]("https://help.ubuntu.com/11.10/ubuntu-help/power-batterywindows.html") and from there are some links for battery settings. If you haven't already read [this webpage]("http://askubuntu.com/questions/400/tips-to-extend-battery-life-for-laptops-and-notebooks") you probably want to. In my limited experience with laptops running linux-there are no easy answers.

---

### Post by N00b-un-2 on 2011-12-06
I had an HP laptop with the same problem.  Battery life was okay at first but the issue was that the battery was defective.  Battery life was slightly better on Windows, but not by much (like 15 minutes more juice).

---

### Post by BC59 on 2011-12-06
Installing Jupiter you could have less problems with battery life:

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

---

