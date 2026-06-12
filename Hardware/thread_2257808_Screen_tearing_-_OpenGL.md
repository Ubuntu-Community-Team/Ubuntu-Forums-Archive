---
title: "Screen tearing - OpenGL"
date: 2014-12-22
forum: Hardware
---

### Post by Da_Panther on 2014-12-22
Hello everyone!

I am having an issue with screen tearing on my Kubuntu 14.04 install. 

Here is my hardware :

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. Device 844d
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f6000000-f70fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e9ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:02.0 Display controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. Device 844d
        Flags: bus master, fast devsel, latency 0, IRQ 53
        Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 54
        Memory at f790a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>
        Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f7908000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 8415
        Flags: bus master, fast devsel, latency 0, IRQ 55
        Memory at f7900000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Prefetchable memory behind bridge: 00000000ea100000-00000000ea1fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: f7800000-f78fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f7907000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 844d
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 51
        I/O ports at f0b0 [size=8]
        I/O ports at f0a0 [size=4]
        I/O ports at f090 [size=8]
        I/O ports at f080 [size=4]
        I/O ports at f060 [size=32]
        Memory at f7906000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: medium devsel, IRQ 14
        Memory at f7905000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f040 [size=32]

[B]01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 625 OEM] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device b590
        Flags: bus master, fast devsel, latency 0, IRQ 56
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at e8000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia[/B]

01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device b590
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 52
        I/O ports at d000 [size=256]
        Memory at ea104000 (64-bit, prefetchable) [size=4K]
        Memory at ea100000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8169

04:00.0 USB controller: ASMedia Technology Inc. Device 1142 (prog-if 30 [XHCI])
        Subsystem: ASUSTeK Computer Inc. Device 85bf
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7800000 (64-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd

```
(in bold is my graphics card).

I have installed and am running the proprietary drivers - Version 331.113 - from NVidia. My screen is connected to the DVI output with a VGA converter... my screen does not have DVI or HDMI ports.

When I go to my system settings, and go to Desktop Effects, I go to the Advanced tab, and at the bottom there is the OpenGL settings section. To stop the screen tearing, I have to manually set Tearing prevention to None, apply, then Full screen repaints. I have no more screen tearing issues ... until I reboot, or take an application or a video to full screen. 

How can I force this setting to be applied at all times, seeing as the NVidia Settings application does not have any options with regards to OpenGL settings for screen tearing?

Thanks, your help is greatly appreciated.

---

### Post by sudodus on 2014-12-23
Did you try another desktop environment or window manager?

In my computers, the video is playing better with LXDE (based on openbox). I have it implemented as Lubuntu (version 14.04.1).

You can try with

```
sudo apt-get install lubuntu-core
```

log out and select session ***lubuntu*** at the log in screen.

---

### Post by Da_Panther on 2015-01-05
Turns out there is a very simple fix. 

Create a file : /etc/profile.d/Tearing.sh

pase one line of code : export __GL_YIELD="USLEEP"

make executable : chmod +x /etc/profile.d/Tearing.sh


Upon reboot, no more screen tearing. :)

---

### Post by sudodus on 2015-01-05
Thanks for sharing your solution :KS

---

