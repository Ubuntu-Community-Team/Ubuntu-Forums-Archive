---
title: "Sony Vaio wireless issue VGN-NR160E"
date: 2010-03-10
forum: Hardware
---

### Post by firewall_03 on 2010-03-10
I am running Karmic 32-bit, I hit suspend or close my laptop up and its hit or miss if my wireless resumes my lspci is this...


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Sony Corporation Device 902d
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Sony Corporation Device 902d
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Sony Corporation Device 902d
        Flags: bus master, fast devsel, latency 0
:

---

### Post by IcarusR on 2010-03-10
Is this with intel wifi ??
If so there is a bug report here..

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297385]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297385")

---

