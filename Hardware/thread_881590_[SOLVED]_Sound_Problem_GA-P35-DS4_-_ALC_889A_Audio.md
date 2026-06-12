---
title: "[SOLVED] Sound Problem GA-P35-DS4 - ALC 889A Audio controller"
date: 2008-08-06
forum: Hardware
---

### Post by bigsur1 on 2008-08-06
Hello,

I have just installed a new kubuntu system and all hardware, except the sound controller seems to be working properly.

I read the threads on this forum concerning this sound chip, but I didnt find a solution, yet.

No device is detected.

My hope was, that the official driver would bring a solution, but when I installed it, I got an error message, that ```
alsa-conf
``` wasnt found.

When I followed the steps in this thread: [http://ubuntuforums.org/showthread.php?p=4653220](http://ubuntuforums.org/showthread.php?p=4653220)
I also didn't get the desired result.

How would you proceed?

Thanks in advance, kind regards

BS

---

### Post by bigsur1 on 2008-08-06
I hit ```
lspci -v
``` in the console and got the following result:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f4000000-f5ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e100 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e200 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f8201000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at e300 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e500 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at f8200000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: medium devsel, IRQ 5
        Memory at f8202000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at e700 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e900 [size=8]
        I/O ports at ea00 [size=4]
        I/O ports at eb00 [size=16]
        I/O ports at ec00 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0312
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f5000000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at b000 [size=256]
        [virtual] Expansion ROM at f4000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0313
        Flags: bus master, fast devsel, latency 0
        Memory at f5010000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f8000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=8]
        I/O ports at c100 [size=4]
        I/O ports at c200 [size=8]
        I/O ports at c300 [size=4]
        I/O ports at c400 [size=16]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at d000 [size=256]
        Memory at f7000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 80000000 [disabled] [size=64K]
        Capabilities: <access denied>

05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at f8104000 (32-bit, non-prefetchable) [size=2K]
        Memory at f8100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Does this mean, that the sound chip is not working? I can find it. I also checked the BIOS and didn't see, where it could be switched off.

Edit: The BIOS setting was hidden to me, I activated it and everything works.

---

