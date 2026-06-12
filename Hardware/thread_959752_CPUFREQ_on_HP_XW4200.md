---
title: "CPUFREQ on HP XW4200"
date: 2008-10-26
forum: Hardware
---

### Post by absolut_nonsense on 2008-10-26
Hi,
The problem:
Adding CPU Frequency Scaling monitor to panel results in 
"CPU Frequency Scaling not supported" error message.
This worked under XP.

Hardware:
CPU: intel Pentium 4 551
```
root@nons-myth:/home/nonsense# cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 1
cpu MHz		: 3400.046
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
bogomips	: 6800.09
clflush size	: 64
power management:
```

MoBo:
```
root@nons-myth:/home/nonsense# lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
05:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
05:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
80:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
```

The very long Description:
I decided to use this xw4200 for my media center.
Since i got lazy, Ubuntu 8.10 was chosen as the base (instead usual Gentoo).
Before Ubuntu installation this machine was running XP Pro and CPU Frequency Scaling worked (Scaled down to 2.6 or 2.8)
Since this feature working on my X31 laptop with 8.10 Live USB I suspect that something wrong with the combination.

Is there any package that I supposed to install/remove?

Thanks.

---

