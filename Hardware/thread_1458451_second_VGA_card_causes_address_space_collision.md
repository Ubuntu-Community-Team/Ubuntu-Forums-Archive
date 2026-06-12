---
title: "second VGA card causes address space collision"
date: 2010-04-20
forum: Hardware
---

### Post by gautamdheeraj on 2010-04-20
I tried to have dual monitor setup. So I bought a new VGA card and put this in my system. But this didn't worked. System->Preferences->Display shows only one monitor. On doing "Detect monitor", it still shows the same monitor.

lspci -v shows the two cards as follows:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: Intel Corporation Device 0c4a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

01:02.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
    Subsystem: ATI Technologies Inc Device 8008
    Flags: stepping, medium devsel, IRQ 77
    Memory at ff000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    I/O ports at c000 [disabled] [size=256]
    Memory at fc900000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Expansion ROM at 40000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: atyfb

Also I tried to change BIOS settings to PCI. The new card work properly. Also in dmsg I found following messages (it seems to me that there is some issue after adding second card.):
gautamd@gautamd-desktop:~$ dmesg| grep colli
[    0.189834] pci 0000:01:02.0: BAR 2: address space collision on of device [0xfffff000-0xffffffff]
[    0.255571] pci 0000:01:02.0: BAR 6: address space collision on of device [0xfffe0000-0xffffffff]

Any help is appreciated.

-Dheeraj

---

