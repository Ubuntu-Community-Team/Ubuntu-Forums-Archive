---
title: "Pinnacle PCTV 310i sound problems..."
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by ehnar on 2008-01-03
I have a problem with my Pinnacle PCTV 310i. I get picture but no sound! I have dual boot with xp and there it works fine with sound, but i like ubuntu better :).

I have tested in terminal  lspci
with following response:
```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:04.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
j
```

Got the idea from another thread here and [HTML]http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i#Firmware[/HTML]

and i also```
lspci -v
```
> 00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 12
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at e0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at e0004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: nVidia Corporation nForce MCP-T Networking Adapter
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: nVidia Corporation Unknown device 4144
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at e0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: 60000000-600fffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation Unknown device 05b2
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: de000000-dfffffff
        Prefetchable memory behind bridge: d0000000-d7ffffff

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: ABIT Computer Corp. Unknown device 8f15
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at df000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:03.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Pinnacle Systems Inc. Unknown device 002f
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at dd001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
        Subsystem: D-Link System Inc DFE-530TX rev C
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at c000 [size=256]
        Memory at dd000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 60000000 [disabled] [size=64K]
        Capabilities: <access denied>



compared to the text at the site mentioned above  a slight difference in output... For the Philips device i get <access denied> what does that mean? 

How can i fix this problem to get the sound work in TVtime or xawTV? Soulution anybody?

PS
No sound cable is connected to the tv-card, was not included in the package when i bought it.
DS

---

