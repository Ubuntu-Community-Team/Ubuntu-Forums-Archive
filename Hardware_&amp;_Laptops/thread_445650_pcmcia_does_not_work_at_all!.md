---
title: "pcmcia does not work at all!"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by acous on 2007-05-16
Hello, I am xubuntu newbie. My PCMCIA port does not work at all. I get this error in dmesg:
cs: unable to map card memory!

and also:

cs: warning: no high memory space available!
cs: unable to map card memory!

Have searched about the problem and found out that I should edit the /etc/pcmcia/config.opts file. But this file does not exist!! So now I am just clueless. What to do?

Installed Xubuntu 6.06.1 (Dapper Drake).

here is output of lspci-v


acous@acous-laptop:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 0 5)
Flags: bus master, medium devsel, latency 0
Memory at f8000000 (32-bit, prefetchable) [size=64M]
Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP] (pr og-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
Memory behind bridge: f4100000-f57fffff
Prefetchable memory behind bridge: 14000000-140fffff

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 1b)
Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
Flags: bus master, stepping, medium devsel, latency 0

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
Flags: bus master, medium devsel, latency 64
I/O ports at 1420 [size=16]
Capabilities: <available only to root>

0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 0e) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
Flags: bus master, medium devsel, latency 64, IRQ 3
I/O ports at 1400 [size=32]
Capabilities: <available only to root>

0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (re v 20)
Flags: medium devsel, IRQ 7

0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 A udio Controller (rev 21)
Subsystem: Compaq Computer Corporation Soundmax integrated digital audio
Flags: medium devsel, IRQ 9
I/O ports at 1000 [size=256]
I/O ports at 1434 [size=4]
I/O ports at 1430 [size=4]
Capabilities: <available only to root>

0000:00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
Subsystem: Compaq Computer Corporation Seminole 1
Flags: medium devsel, IRQ 11
Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
I/O ports at 1438 [size=8]
Capabilities: <available only to root>

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 01)
Subsystem: Compaq Computer Corporation: Unknown device b103
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at 14100000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
Memory window 0: 10000000-11fff000 (prefetchable)
Memory window 1: 12000000-13fff000
I/O window 0: 00001800-000018ff
I/O window 1: 00001c00-00001cff
16-bit legacy interface ports at 0001

0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a) (prog-if 00 [VGA])
Subsystem: Compaq Computer Corporation CyberBlade i1 AGP
Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 64, IRQ 9
Memory at f5000000 (32-bit, non-prefetchable) [size=8M]
Memory at f4100000 (32-bit, non-prefetchable) [size=128K]
Memory at f4800000 (32-bit, non-prefetchable) [size=8M]
Expansion ROM at 14000000 [disabled] [size=64K]
Capabilities: <available only to root>

---

### Post by harsto on 2008-01-04
Did you solve the problem in the meantime? I just have checked a similar issue, maybe I can help.

so long
harsto

---

