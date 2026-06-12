---
title: "Problems with ubuntu 20.04 graphics drivers"
date: 2020-05-19
forum: Hardware
---

### Post by yanunim95 on 2020-05-19
I have system with 2 video cards.
Each video card is attached to separate displays.
5500XT is attached to 4K display via Display port.
R7 250 is attached to older monitor via DVI.


If i set in mate display settings older display as primary it looks like R7 250 goes in power saving mode.
Temperature for R7 in lm-sensors goes down to 25-30°C.
If i move chromium window with youtube to display attached to R7, i'm getting 1 frame per 15-20 seconds.
Even text input in askubuntu feels laggy.
Same window on display attached to 5500XT works fine.


If i make as primary display attached to 5500XT everything works fine.
chromium window with youtube does not drops frames on monitor attached to R7.
lm-sensors shows that temperature does to ~32°C if nothing is rendered and ~38°C with chromium and youtube.
First i thought that problem is in IOMMU options, that i'm giving to kernel via grub.
But removing GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt " options also not helped.


I have also checked it with SMPlayer with different videos.
It is also laggy over R7 when display attached to R7 is set as primary output.


So my questions:


How can it be debugged?
Is it bug?
Mate bug?
Ubuntu?
Xorg?
Should it be reported to ubuntu developers?
Is it a feature?
Can i configure this feature?
System spec:



[LIST]
[*]OS: Ubuntu 20.04
[*]CPU: Ryzen 7 1700
[*]M/B: Asus TUF B450m-Pro
[*]Video: Sapphire 5500 XT(main pcie slot), PowerColor r7 250(chipset pcie slot).
[/LIST]

Drivers information:5500XT:
```
unim95@unim95-PC:~$ cat /sys/class/drm/card1/device/uevent 
DRIVER=amdgpu
PCI_CLASS=30000
PCI_ID=1002:7340
PCI_SUBSYS_ID=1DA2:E421
PCI_SLOT_NAME=0000:09:00.0
MODALIAS=pci:v00001002d00007340sv00001DA2sd0000E421bc03sc00i00

```R7 250
```
unim95@unim95-PC:~$ cat /sys/class/drm/card0/device/uevent 
DRIVER=radeon
PCI_CLASS=30000
PCI_ID=1002:6610
PCI_SUBSYS_ID=1787:2334
PCI_SLOT_NAME=0000:06:00.0
MODALIAS=pci:v00001002d00006610sv00001787sd00002334bc03sc00i00

```

lspci shows following
```

06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Oland XT [Radeon HD 8670 / R7 250/350] [1002:6610] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Oland XT [Radeon HD 8670 / R7 250/350] [1787:2334]
    Flags: bus master, fast devsel, latency 0, IRQ 97
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc900000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=256]
    Expansion ROM at fc940000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu


06:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series] [1002:aab0]
    Subsystem: Hightech Information System Ltd. Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series] [1787:aab0]
    Flags: bus master, fast devsel, latency 0, IRQ 102
    Memory at fc960000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


07:00.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 XL Upstream Port of PCI Express Switch [1002:1478] (rev c5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 39
    Memory at fcd00000 (32-bit, non-prefetchable) [size=16K]
    Bus: primary=07, secondary=08, subordinate=09, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff [size=4K]
    Memory behind bridge: fcc00000-fccfffff [size=1M]
    Prefetchable memory behind bridge: 00000000c0000000-00000000d01fffff [size=258M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


08:00.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 XL Downstream Port of PCI Express Switch [1002:1479] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Bus: primary=08, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff [size=4K]
    Memory behind bridge: fcc00000-fccfffff [size=1M]
    Prefetchable memory behind bridge: 00000000c0000000-00000000d01fffff [size=258M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


09:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 14 [Radeon RX 5500/5500M / Pro 5500M] [1002:7340] (rev c5) (prog-if 00 [VGA controller])
    Subsystem: Sapphire Technology Limited Navi 14 [Radeon RX 5500/5500M / Pro 5500M] [1da2:e421]
    Flags: bus master, fast devsel, latency 0, IRQ 98
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at f000 [size=256]
    Memory at fcc00000 (32-bit, non-prefetchable) [size=512K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu


09:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 HDMI Audio [1002:ab38]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 HDMI Audio [1002:ab38]
    Flags: bus master, fast devsel, latency 0, IRQ 104
    Memory at fcca0000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```

Can it be cause of R7 250 is some how tries to use both drivers amdgpu and radeon drivers?


**Small UPD**
Now i'm getting graphics glitches on desktop.

---

