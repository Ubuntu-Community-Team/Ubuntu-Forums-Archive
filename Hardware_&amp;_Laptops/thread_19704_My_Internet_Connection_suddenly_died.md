---
title: "My Internet Connection suddenly died"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by mhykhh on 2005-03-13
I dont know what I did wrong but my internet suddenly died. I could not activate my 3com ethernet card on the Networking window.

here's the output of lspci -v

> 
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
        Subsystem: Asustek Computer, Inc.: Unknown device 8070
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ee000000-efdfffff
        Prefetchable memory behind bridge: eff00000-f7ffffff

0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Bridge (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: ec800000-edffffff
        Prefetchable memory behind bridge: efe00000-efefffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 12)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 12) (prog-if 80 [Master])
        Subsystem: Asustek Computer, Inc.: Unknown device 8028
        Flags: bus master, medium devsel, latency 0
        I/O ports at b800 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8028
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at b400 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 12)
        Subsystem: Asustek Computer, Inc.: Unknown device 8028
        Flags: medium devsel, IRQ 185
        I/O ports at 1000 [size=16]

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8028
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at b000 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 12)
        Subsystem: Asustek Computer, Inc.: Unknown device 8072
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at a800
        I/O ports at a400 [size=64]

0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2) (prog-if 00 [VGA])
        Subsystem: Asustek Computer, Inc.: Unknown device 406b
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at ee000000 (32-bit, non-prefetchable) [size=efff0000]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at 00010000 [disabled]
        Capabilities: <available only to root>

0000:02:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)
        Subsystem: 3Com Corporation 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at d800 [disabled]
        Memory at ed800000 (32-bit, non-prefetchable) [disabled] [size=128]
        Capabilities: <available only to root>

0000:02:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: Conexant: Unknown device 2003
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ed000000 (32-bit, non-prefetchable) [disabled]
        I/O ports at d400 [disabled] [size=8]
        Capabilities: <available only to root>

0000:02:0c.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
        Subsystem: Unknown device 4554:434e
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at d000 [disabled]
        Memory at ec800000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <available only to root>
 

My internet used to be working perfectly. Now the only problem is activating my ethernet cards. I dont know if I'm missing some modules or packages but I really cant activate them.

---

### Post by alastair on 2005-03-13
Logs ...

Look in /var/log/syslog and see if there are any relevant (ethernet/eth) errors or messages.

---

