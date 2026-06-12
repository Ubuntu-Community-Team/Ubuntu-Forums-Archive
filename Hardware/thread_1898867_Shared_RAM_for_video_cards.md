---
title: "Shared RAM for video cards"
date: 2011-12-22
forum: Hardware
---

### Post by manolomanolo on 2011-12-22
Hi to all.

How can I see how much RAM has been assigned to my video card?
Thanks

---

### Post by d2btoo on 2011-12-22
```

fgrep -i videoram /var/log/Xorg.0.log

```

```

lspci -v
*and look for the VGA section*

```

---

### Post by manolomanolo on 2011-12-22
Hi d2betoo. Thanks for yr reply.
I got no result when executing **fgrep -i videoram /var/log/Xorg.0.log**
On the other hand, this is what I get when running **lspci -v** and I can see no information about how much RAM is used by my video card.

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0
        Memory at f8400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141                                                                                                                              
        Flags: bus master, medium devsel, latency 0, IRQ 20                                                                                                                         
        I/O ports at 1860 [size=32]                                                                                                                                                 
        Capabilities: <access denied>                                                                                                                                               
        Kernel driver in use: uhci_hcd                                                                                                                                              
                                                                                                                                                                                    
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at f8904800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f8900000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f8500000-f85fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: f8600000-f86fffff
        Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: c0200000-c03fffff
        Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f4000000-f5ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1880 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 18a0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 18c0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f8904c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
        I/O ports at 1818 [size=8]
        I/O ports at 180c [size=4]
        I/O ports at 1810 [size=8]
        I/O ports at 1808 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8904000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: medium devsel, IRQ 10
        Memory at c0100000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]
        Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Foxconn International, Inc. Device e006
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

---

### Post by Ptero-4 on 2011-12-22
> **manolomanolo said:**
> Hi d2betoo. Thanks for yr reply.
I got no result when executing **fgrep -i videoram /var/log/Xorg.0.log**
On the other hand, this is what I get when running **lspci -v** and I can see no information about how much RAM is used by my video card.

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f8000000 (64-bit, non-prefetchable) [[COLOR="DarkOrange"]size=4M[/COLOR]]
        Memory at d0000000 (64-bit, prefetchable) [[COLOR="Red"]size=256M[/COLOR]]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0
        Memory at f8400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141                                                                                                                              
        Flags: bus master, medium devsel, latency 0, IRQ 20                                                                                                                         
        I/O ports at 1860 [size=32]                                                                                                                                                 
        Capabilities: <access denied>                                                                                                                                               
        Kernel driver in use: uhci_hcd                                                                                                                                              
                                                                                                                                                                                    
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at f8904800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f8900000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f8500000-f85fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: f8600000-f86fffff
        Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: c0200000-c03fffff
        Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f4000000-f5ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1880 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 18a0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 18c0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f8904c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
        I/O ports at 1818 [size=8]
        I/O ports at 180c [size=4]
        I/O ports at 1810 [size=8]
        I/O ports at 1808 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8904000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: medium devsel, IRQ 10
        Memory at c0100000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]
        Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
        Subsystem: Acer Incorporated [ALI] Device 0141
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Foxconn International, Inc. Device e006
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```
Thee ones in red and orange are the ram your video card is using (prefetchable and non-prefetchable respectivelly).

---

### Post by manolomanolo on 2011-12-24
Ok, so I have a bigger problem. I started **[here]("http://ubuntuforums.org/showthread.php?t=1895107")** some days ago by asking why the system told my it is just using 3 of the 4GB of installed RAM.
ACER support team told me it is because the video card is automatically using the other 1GB.

So, it seems the system is just giving 256MB to the video card, not 1GB as ACER support said. Right?


PD: is that 256MB on board memory (I mean, installed on the video card) or is it part of those 4GB?

---

