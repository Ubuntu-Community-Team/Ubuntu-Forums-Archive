---
title: "No sound in Ubuntu 7.10"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by speedisso on 2007-10-31
hi  all i really need help

I just installed ubuntu 7.10 and i have no sound, my audio card is reconized but i can hear any sound...pls help me
Here is my lspci -v

```
cmalexandru@laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 90000000-afffffff
        Prefetchable memory behind bridge: c0000000-cfffffff
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b0000000-b3ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 4800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 4820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 4840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 4860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: b4000000-b40fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 5000 [size=256]
        I/O ports at 4880 [size=64]
        Memory at 80000800 (32-bit, non-prefetchable) [size=512]
        Memory at 80000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Rioworks Unknown device 2047
        Flags: medium devsel, IRQ 19
        I/O ports at 5400 [size=256]
        I/O ports at 4c00 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 48f0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
        Subsystem: Rioworks Unknown device 2047
        Flags: medium devsel, IRQ 10
        I/O ports at 4ca0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1) (prog-if 00 [VGA])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at a0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 91000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
        Subsystem: Rioworks Marvell 88E8053 Gigabit Ethernet Controller (Arima)
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 6000 [size=256]
        [virtual] Expansion ROM at d0000000 [disabled] [size=128K]
        Capabilities: <access denied>

06:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at b4009000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

06:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at b4006000 (32-bit, non-prefetchable) [size=2K]
        Memory at b4000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at b4004000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:02.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Rioworks Unknown device 2047
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at b4007000 (32-bit, non-prefetchable) [size=256]
        Memory at b4006c00 (32-bit, non-prefetchable) [size=256]
        Memory at b4006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2702
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at b4008000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

cmalexandru@laptop:~$ 


```

I tried all the tuts that i found here none works for me

---

### Post by mrukus on 2007-10-31
just try this, it worked on my laptop. apprently the speakers were through the surround channel, so fiddle around and make sure all the levels are up, and non are accidently muted.  i really new to ubuntu and linux so thats all i got for ya, hope i helped a little bit

---

### Post by speedisso on 2007-10-31
i already checked and they were muted but it doesn´t work anyway...pls someone of the geeks...just say something

---

### Post by Therion on 2007-10-31
Have you seen this post/thread?

[[color=blue]Comprehensive Sound Problems[/color]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

---

