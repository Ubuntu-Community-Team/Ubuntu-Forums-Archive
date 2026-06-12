---
title: "What has USB to do with my soundcard?"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by onnest on 2007-07-07
I have a Asrock 939 dual sata2 mobo with onboard soundcard (realtek 850).
Here's the thing, I can only get sound from my speakers (wich are connected to the soundcard) if my usb-headset is plugged in at boot.

If its not plugged in I can still listen to music i Rythmbox or watch movies i Totem if Sound Preferenses are all set to "USB Audio", but I have no system sound (login-sound etc.).
I can not start alasamixer in this case.

Can someone explain this strange behavior?

What I ultimately would like to do is to get Ubuntu to recognize my soundcard, which it doesn't seem to do. Or, get sound working without the need to have a usb-headset plugged in.

# lspci -v
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation PCI Express Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Prefetchable memory behind bridge: d7e00000-d7efffff
        Capabilities: <access denied>

00:02.0 PCI bridge: ALi Corporation PCI Express Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Prefetchable memory behind bridge: d7f00000-d7ffffff
        Capabilities: <access denied>

00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
        Flags: bus master, fast devsel, latency 0
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:05.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        Memory behind bridge: f6f00000-f7ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff

00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32

00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
        Subsystem: ASRock Incorporation Unknown device 1563
        Flags: bus master, medium devsel, latency 0

00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ASRock Incorporation Unknown device 7101
        Flags: medium devsel

00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
        Subsystem: ASRock Incorporation Unknown device 5263
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at e800 [size=256]
        Memory at f6effc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard IDE (PATA)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 5237
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at f6efe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 5237
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at f6efd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 5237
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at f6efc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 5239
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        Memory at f6eff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

03:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900] (rev a1) (prog-if 00 [VGA])
        Subsystem: Creative Labs Unknown device 9371
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
        Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at f6fe0000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by onnest on 2007-07-08
bump

---

