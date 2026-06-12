---
title: "broadcom 802.11n driver/dual video card question"
date: 2014-11-19
forum: Hardware
---

### Post by creatxr on 2014-11-19
i installed xubuntu 14.04 today.
it didn't find the wireless card: broadcom 802.11n.

my laptop has two video card.
can xubuntu do save power as windows? (let one video card to sleep if it's not useful.)

thanks

---

### Post by ajgreeny on 2014-11-19
For wireless problem let's see the output of **lspci** in terminal to find the chipset of the card; we can then tell you how to proceed.

For the video, is this an optimus hybrid system from nvidia, or the AMD equivalent?

---

### Post by Frogs Hair on 2014-11-19
Below is my Broadcom card and it works out of the box. There is a driver available in additional drivers , but the kernel included driver has always worked fine. The output of the command posted by ajgreeny will clarify what card and rev you have.
```
Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)

```

---

### Post by creatxr on 2014-11-19
03:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

---

### Post by creatxr on 2014-11-19
i didn't find where can i download the driver, it seems that the links are no longer good

---

### Post by Frogs Hair on 2014-11-19
Open Software & Updates and navigate to the additional drivers tab and when open the utility will search for drivers.

---

### Post by creatxr on 2014-11-20
thanks.
wireless works.
other question: will xubuntu auto use power saving video card?

---

### Post by Frogs Hair on 2014-11-20
> will xubuntu auto use power saving video card? 				

I don't know the answer to that one so, bump the thread as needed until you get an answer. The following command should list the video card/s info first. ```
lspci -v
```

---

### Post by creatxr on 2014-11-20
it seems that the power lost quickly.   

[PHP]
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Intel Corporation Device 2010
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f7a14000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 201f
    Flags: bus master, medium devsel, latency 0, IRQ 46
    Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f7a1c000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7900000-f79fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7800000-f78fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 48
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a1a000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: medium devsel, IRQ 255
    Memory at f7a19000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]

01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 178d
    Flags: fast devsel, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
    Subsystem: Lite-On Communications Inc Device 6605
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7900000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: wl

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 202f
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7815000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at f7800000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci

04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device 200f
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at d000 [size=256]
    Memory at f7814000 (64-bit, non-prefetchable) [size=4K]
    Memory at f7810000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169


[/PHP]

---

