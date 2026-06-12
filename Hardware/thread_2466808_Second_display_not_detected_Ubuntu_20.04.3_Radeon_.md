---
title: "Second display not detected Ubuntu 20.04.3 Radeon RX Vega56"
date: 2021-09-06
forum: Hardware
---

### Post by absurdramon on 2021-09-06
Hello everyone.  I'm testing Ubuntu 20.04.3 with the goal of switching from Windows 10 to Linux.  Everything is working fine except my second display which stays in power-save mode. It was working fine in Windows but for whatever reason Ubuntu isn't detecting the second monitor.  The Display settings screen only shows the one display.  I've been searching the Internet for a solution but nothing as of yet has worked.  I've tried reinstalling Ubuntu, updated the amdgpu drivers from both AMD's website and through PPA, tried using Kubuntu and Pop-OS but no change.

My system build is as follows:
Motherboard: MSI X470
CPU: AMD Ryzen 7 2700x
Memory: 32GB
GPU: MSI AMD Radeon RX Vega56
Display 1: Acer V246HQL connected via DVI>DVI/DP adapter>DP port 2 (this is the working monitor)
Display 2: ViewSonic XG2402 connected via HDMI>HDMI port 0 (this is the one that stays asleep)

One little quirk I want to mention that may/may not be related, but when my system boots up it defaults to the Acer display until the Windows logon, at which point it switches to the ViewSonic display as the primary.

Here's some more information about my system:

```
utest@utest-MS-7B78:~$ sudo lshw -c video
[sudo] password for utest: 
  *-display                 
       description: VGA compatible controller
       product: Vega 10 XL/XT [Radeon RX Vega 56/64]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:1e:00.0
       logical name: /dev/fb0
       version: c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:a0-9f iomemory:90-8f irq:79 memory:a00000000-bffffffff memory:900000000-9001fffff ioport:e000(size=256) memory:fe400000-fe47ffff memory:fe480000-fe49ffff

```

I am a Linux novice and am at a complete loss.  I hope someone here can guide me to fixing this.

---

### Post by absurdramon on 2021-09-22
I'm really surprised no one has responded yet.  Please help.  If I need to provide more information about my system, just ask.

---

