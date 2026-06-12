---
title: "Lenovo 3000 N100 Sound does not work"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by mlh on 2006-06-12
Hi everyone, I have a brand new Lenovo 3000 N100.  Sound does not work.  It sees a hda intel card in the control panel and nothing is muted at all.    Please try and help me.

Here is some debug info
uname -a
Linux laptop 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xb0000000 irq 233

lspci -v
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Lenovo: Unknown device 2061
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [5109]

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Lenovo: Unknown device 2062
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Lenovo: Unknown device 2062
        Flags: bus master, fast devsel, latency 0
        Memory at b0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo: Unknown device 2066
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: b0200000-b02fffff
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo: Unknown device 206b
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo: Unknown device 206c
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo: Unknown device 206d
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo: Unknown device 206e
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Lenovo: Unknown device 206f
        Flags: bus master, medium devsel, latency 0, IRQ 217
        Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: b0300000-b03fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031f00000
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Lenovo: Unknown device 2071
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] #09 [100c]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Lenovo: Unknown device 2072
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Lenovo: Unknown device 2073
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

0000:03:00.0 Network controller: Intel Corporation: Unknown device 4227 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1010
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at b0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] #10 [0011]

0000:05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Lenovo: Unknown device 2074
        Flags: bus master, medium devsel, latency 64, IRQ 50
        I/O ports at 2000 [size=256]
        Memory at b0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Lenovo: Unknown device 2075
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at b0301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 32000000-33fff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        16-bit legacy interface ports at 0001

0000:05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Lenovo: Unknown device 2076
        Flags: bus master, medium devsel, latency 64, IRQ 233
        Memory at b0300800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

0000:05:06.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Lenovo: Unknown device 2077
        Flags: bus master, medium devsel, latency 64, IRQ 217
        Memory at b0300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:05:06.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
        Subsystem: Lenovo: Unknown device 2078
        Flags: medium devsel, IRQ 7
        Memory at b0302000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

0000:05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Lenovo: Unknown device 2079
        Flags: medium devsel, IRQ 7
        Memory at b0302400 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

0000:05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Lenovo: Unknown device 207a
        Flags: medium devsel, IRQ 7
        Memory at b0302800 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

---

### Post by spotman on 2006-06-12
Is your modem disabled in the bios?  Re-enabling that solved this issue for me on my lenovo T60.

Good luck, and I hear another workaround for a weird snd_hda_intel problem is to recompile without alsa support in your kernel, and then manually grab the latest alsa cvs from their site.

---

### Post by spotman on 2006-06-12
also you might want to try alsaconf, although im not sure its installed in dapper by default.

---

### Post by wjp.reg on 2006-06-12
This worked for me..

[http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10]("http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10")

---

