---
title: "No sound after fresh install of Ubuntu 17.10."
date: 2018-03-11
forum: Hardware
---

### Post by mar-macatunao on 2018-03-11
Hello guys, badly needing your help.  I performed a fresh installation of Ubuntu 17.10 in my Zeus lapbook (Chuwi?).  All is working fine except there is no sound.
I am very frustrated to find the answer to this problem.  I came from Windows 10 and I don't wanna go back.  I want to keep 17.10 as my sole OS in my laptop.
Seems like no audio device is detected.  Output of "lspci -v" is as follows:  Thank you in advanced!!! ;)

mar@mar-zeus-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: iosf_mbi_pci


00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
    Flags: bus master, fast devsel, latency 0, IRQ 298
    Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit
    Flags: fast devsel, IRQ 255
    Memory at 91000000 (32-bit, non-prefetchable) [disabled] [size=4M]
    Capabilities: <access denied>


00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
    Flags: fast devsel, IRQ 343
    Memory at 9183b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device


00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36) (prog-if 30 [XHCI])
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 297
    Memory at 91800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
    Flags: bus master, fast devsel, latency 0, IRQ 344
    Memory at 91700000 (32-bit, non-prefetchable) [size=1M]
    Memory at 91600000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: mei_txe
    Kernel modules: mei_txe


00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)
    Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

---

