---
title: "NVIDIA graphics driver gone"
date: 2021-01-19
forum: Hardware
---

### Post by claus on 2021-01-19
Hi,

since today, all-of-a-sudden the driver for my NVIDIA GeForce GT 710 graphics card is missing. In 'About this computer' under 'Graphics' there is 'llvmpipe (LLVM 10.0.0, 128 bits)' instead of the NVIDIA card. What can I do to install the proper driver anew?

TIA,

Claus

---

### Post by Frogs Hair on 2021-01-19
Post the output of the following command. Check additional drivers for changes.```
 lspci -v
```

---

### Post by claus on 2021-01-19
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
    Subsystem: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
    Flags: fast devsel

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 IOMMU
    Subsystem: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 IOMMU
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Capabilities: <access denied>

00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
    Flags: fast devsel

00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff [size=4K]
    Memory behind bridge: f6000000-f70fffff [size=17M]
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff [size=160M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=12, subordinate=28, sec-latency=0
    I/O behind bridge: 0000e000-0000efff [size=4K]
    Memory behind bridge: f7600000-f77fffff [size=2M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
    Flags: fast devsel

00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Bus: primary=00, secondary=29, subordinate=29, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: f7200000-f75fffff [size=4M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus B (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Bus: primary=00, secondary=2a, subordinate=2a, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: f7800000-f78fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH SMBus Controller
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 0
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 3
    Flags: fast devsel
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 5
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 6
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 7
    Flags: fast devsel

10:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation GK208B [GeForce GT 710]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at f000 [size=128]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau

10:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation GK208 HDMI/DP Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 60
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

12:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43bc (rev 02) (prog-if 30 [XHCI])
    Subsystem: ASMedia Technology Inc. Device 1142
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f77a0000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

12:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b8 (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASMedia Technology Inc. Device 1062
    Flags: bus master, fast devsel, latency 0, IRQ 56
    Memory at f7780000 (32-bit, non-prefetchable) [size=128K]
    Expansion ROM at f7700000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

12:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Bus: primary=12, secondary=20, subordinate=28, sec-latency=0
    I/O behind bridge: 0000e000-0000efff [size=4K]
    Memory behind bridge: f7600000-f76fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

20:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Bus: primary=20, secondary=25, subordinate=25, sec-latency=0
    I/O behind bridge: 0000e000-0000efff [size=4K]
    Memory behind bridge: f7600000-f76fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

20:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Bus: primary=20, secondary=26, subordinate=26, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: [disabled]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

20:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Bus: primary=20, secondary=27, subordinate=27, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: [disabled]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

20:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Bus: primary=20, secondary=28, subordinate=28, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: [disabled]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 32
    I/O ports at e000 [size=256]
    Memory at f7604000 (64-bit, non-prefetchable) [size=4K]
    Memory at f7600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

29:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Zeppelin/Raven/Raven2 PCIe Dummy Function (rev c9)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Zeppelin/Raven/Raven2 PCIe Dummy Function
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

29:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7400000 (32-bit, non-prefetchable) [size=1M]
    Memory at f7508000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

29:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Raven USB 3.1 (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Raven USB 3.1
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7300000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

29:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Raven USB 3.1 (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Raven USB 3.1
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f7200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

29:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
    Subsystem: Micro-Star International Co., Ltd. [MSI] Family 17h (Models 10h-1fh) HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 61
    Memory at f7500000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

2a:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. [MSI] FCH SATA Controller [AHCI mode]
    Flags: bus master, fast devsel, latency 0, IRQ 59
    Memory at f7800000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci
```

---

### Post by Frogs Hair on 2021-01-19
Your card is identified and appears to be using the nouveau driver. Is there a proprietary driver available in additional drivers? My GT730 uses the 390 driver. 


```
10:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation GK208B [GeForce GT 710]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at f000 [size=128]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau
```

---

### Post by claus on 2021-01-19
Is there a proprietary driver available in additional drivers? My GT730 uses the 390 driver. 

Yes, I could find the 390 driver, but when I attempted to install it I was notified that there is a bunch of unmet dependencies. How shall I proceed?

Claus

---

### Post by CatKiller on 2021-01-19
> **claus said:**
> My GT730 uses the 390 driver.

The 390 branch is the Legacy branch for no-longer-supported cards. Since you haven't said which release you're using, I'll assume you're on 20.04, are using the HWE stack, and have recently upgraded to the 5.8 branch kernel that the Legacy Nvidia driver doesn't work with.

The 710 (and the 730 for that matter, although I assume that's a typo) is supported by current drivers. The 455 and 460 branches are the current ones. It's generally best to purge all the Nvidia stuff before moving to a different branch.

---

### Post by claus on 2021-01-19
> **CatKiller said:**
> It's generally best to purge all the Nvidia stuff before moving to a different branch.

I understand, but how do I clean up the installed Nvidia packages? I took a look using Synaptic, and I have a number of packages for the Nvidia 440 driver installed. Do I have to uninstall all of them manually using Synaptic, or can it be done via shell? I already (unsuccessfully) tried 'sudo apt install nvidia-driver-455', but there are a number of unmet dependencies. So I guess I have to first get rid of the 440 stuff before installing the 455 driver. I also wonder how this problem came about in the first place. Until this morning everything worked just fine. (Ok, I re-read your post. It must have been due to an update.)

Claus

---

### Post by Frogs Hair on 2021-01-19
> [COLOR=#000000](and the 730 for that matter, although I assume that's a typo)[/COLOR] No not a typo , the 730 is a similar card depending on vendor.

---

### Post by CatKiller on 2021-01-19
> **Frogs Hair said:**
> No not a typo , the 730 is a similar card depending on vendor.

Ah, I hadn't spotted that those were your words given by the OP without quote tags.

---

### Post by CatKiller on 2021-01-19
> **claus said:**
> I understand, but how do I clean up the installed Nvidia packages? I took a look using Synaptic, and I have a number of packages for the Nvidia 440 driver installed. Do I have to uninstall all of them manually using Synaptic, or can it be done via shell?

```
sudo apt-get purge nvidia* libnvidia*
``` should do it. 

> I already (unsuccessfully) tried 'sudo apt install nvidia-driver-455', but there are a number of unmet dependencies.

Details of what those unmet dependencies are would be helpful; the 440 branch isn't the Legacy branch, but the problem might still have been triggered by the 5.8 update, or it might be something else.

---

### Post by claus on 2021-01-19
> **CatKiller said:**
> Details of what those unmet dependencies are would be helpful

Here goes:

The following packages have unmet dependencies:
 nvidia-driver-455 : Depends: libnvidia-decode-455 (= 455.45.01-0ubuntu0.20.04.1) but it is not going to be installed
                     Depends: libnvidia-encode-455 (= 455.45.01-0ubuntu0.20.04.1) but it is not going to be installed
                     Depends: libnvidia-fbc1-455 (= 455.45.01-0ubuntu0.20.04.1) but it is not going to be installed
                     Recommends: libnvidia-compute-455:i386 (= 455.45.01-0ubuntu0.20.04.1)
                     Recommends: libnvidia-decode-455:i386 (= 455.45.01-0ubuntu0.20.04.1)
                     Recommends: libnvidia-encode-455:i386 (= 455.45.01-0ubuntu0.20.04.1)
                     Recommends: libnvidia-fbc1-455:i386 (= 455.45.01-0ubuntu0.20.04.1)
E: Unable to correct problems, you have held broken packages.

Claus

P. S.: After a reboot, the display is at 1920 x 1080 again, and my Philips monitor is being recognized. Now I have to install the 455 driver.

---

### Post by Frogs Hair on 2021-01-20
I would suggest making sure the computer is up to date. ```
sudo apt update && sudo apt upgrade  
```

---

### Post by mastablasta on 2021-01-21
> **CatKiller said:**
> 
The 710 (and the 730 for that matter, although I assume that's a typo) is supported by current drivers. The 455 and 460 branches are the current ones. It's generally best to purge all the Nvidia stuff before moving to a different branch.

actually not. only some versions of 730 have new driver support.

also as i understand it it should still be supported by new kernel, and i was hoping also in 22.04 LTS

[https://nvidia.custhelp.com/app/answers/detail/a_id/3142](https://nvidia.custhelp.com/app/answers/detail/a_id/3142)

> [COLOR=#000000][FONT=&quot]The Linux 390.* legacy driver series is the last to support GF1xx ("Fermi") GPUs.  Support for new Linux kernels and X servers, as well as fixes for critical bugs, will be included in 390.* legacy releases through the end of 2022.[/FONT][/COLOR]
[TABLE="width: 100%, align: left"]
[TR]
[TD="class: text, width: 32%"]**NVIDIA GPU product**[/TD]
[TD="class: text, width: 32%"]**Device PCI ID**[/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%, align: left"]
[TR]
[TD="class: text, width: 32%"]GeForce GT 730[/TD]
[TD="class: text, width: 32%"]0F02

[/TD]
[/TR]
[/TABLE]

---

