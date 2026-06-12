---
title: "Samsung R20 freezes with 2.6.22"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by hackeron on 2007-08-10
I have a Samsung R20 laptop and ever since upgrading to 2.6.21 (and same with 2.6.22 on gutsy), my machine freezes within the first few minutes after boot unless I disable CPU frequency scaling with something like:

```

cpufreq-selector -c 0 -g performance

```

There is nothing in /var/log/messages or /var/log/syslog to suggest what is causing the crash and I'm not sure how to troubleshoot this further so any ideas would be appreciated.

Here's my cpuinfo:

```

# cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
stepping        : 8
cpu MHz         : 1733.329
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe constant_tsc up pni monitor tm2 xtpr
bogomips        : 3469.90
clflush size    : 64

```

Here's my lspci:

```

# lspci -v
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7930
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7932 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff
        Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 7932

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7935 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 7930
        Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7936 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Memory behind bridge: d0200000-d02fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 7930
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 8438 [size=8]
        I/O ports at 8444 [size=4]
        I/O ports at 8430 [size=8]
        I/O ports at 8440 [size=4]
        I/O ports at 8400 [size=16]
        Memory at d0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0007000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0008000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0009000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at d0004400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0300000-d03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 7942 (prog-if 00 [VGA])
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, fast devsel, latency 64, IRQ 19
        Memory at d4000000 (64-bit, prefetchable) [size=64M]
        Memory at d0100000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 9000 [size=256]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7108
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at d0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

08:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Samsung Electronics Co Ltd Unknown device c511
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at a000 [size=256]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

```

---

