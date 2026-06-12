---
title: "Ethernet Controller Marvell Technology Group Ltd Unknown device 4351 (rev 10)"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by Anouar on 2006-03-29
Hi Guys,
I would like to introduce my self and my laptop:) 
My name is Anouar , I come from Holland.
I studie Computer Science at the Academy in Enschede

My Laptop, is a Toshiba M40-155 2.0 Ghz 512mb MEM , 100Gb HD Dual L DVD Burner

Well, lets go, the problem is that my network controller is'nt recongnized by ubuntu while installing.

So i ignored that and installed it from the CD-rom.

But now i still can't get my network controller working,
My intel Pro/Wireless has worked one time, but then the game was over

I have read various articles about linux headers and install scripts, e.g
[http://www.achilleus.net/LinuxToshiba.html](http://www.achilleus.net/LinuxToshiba.html)
also tried:

[http://www.ubuntuforums.org/showthread.php?t=47615&highlight=marvell+failed](http://www.ubuntuforums.org/showthread.php?t=47615&highlight=marvell+failed)

But i cant find the headers, and even i  could find them I still don't know how to install them

I have a Working USB Stick

Can any one help me?

It would be great.

Thanx in advance

Anouar

---

### Post by mips on 2006-03-29
Post the output of **lspci -v** here. Would like to know the chipset version if at all recognised.

---

### Post by Anouar on 2006-03-30
[SIZE="7"][COLOR="Sienna"]Hi [/COLOR][/SIZE][COLOR="Sienna"]**[SIZE="5"]mips[/SIZE]**[/COLOR]
Thnx for your post,
[COLOR="Sienna"]
Guys, this is my lspci -v  [/COLOR]

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: c0000000-cfffffff
        Prefetchable memory behind bridge: 90000000-9fffffff
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 000000008c000000-000000008ff00000
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: b8000000-bbffffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bf00000
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1200 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1220 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1240 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1260 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4) (prog-if 01 [Subt ractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: b0000000-b7ffffff
        Prefetchable memory behind bridge: 0000000080000000-0000000087f00000
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=64]
        Memory at d0000000 (32-bit, non-prefetchable) [size=512]
        Memory at d0000200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 5
        I/O ports at e200 [size=256]
        I/O ports at e300 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 0

0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04 ) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1100 [size=16]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 315 0 (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at 90000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at bc000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <available only to root>

0000:06:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2741
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at b000b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 20000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032 (prog- if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 6
        Memory at b0000000 (32-bit, non-prefetchable) [size=2K]
        Memory at b0004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:06:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at b0008000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:06:06.4 0805: Texas Instruments: Unknown device 8034
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at b000a000 (32-bit, non-prefetchable) [size=256]
        Memory at b000a100 (32-bit, non-prefetchable) [size=256]
        Memory at b000a200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

---

### Post by Anouar on 2006-04-01
Hi guys,

I finally have wireless internet,

So maby it is easier te help me now

Anouar

---

### Post by mips on 2006-04-01
[QUOTE=Anouar]
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at bc000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <available only to root>
[/QUOTE]


Ok so it is the Marvell Chipset. We just need to check which exact chipset that specific Toshiba uses.

---

### Post by Anouar on 2006-04-01
So  how do I find out what chipset it is?](*,)

---

### Post by mips on 2006-04-03
If your machine is dualboot you could have a look in windows. Alternatively the toshiba europe website.

It uses a **Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller**

---

### Post by Anouar on 2006-04-16
Well , guys,

I did my best to find a driver, too bad i still can't find one.

Sugestions?

Anouar

---

### Post by daller on 2007-01-19
> **mips said:**
> If your machine is dualboot you could have a look in windows. Alternatively the toshiba europe website.

It uses a **Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller**

Is there no way to find the chipset name on the board?

---

### Post by mips on 2007-01-19
> **daller said:**
> Is there no way to find the chipset name on the board?

Do you want to open the laptop ? Might be wrtten on the chip.

---

### Post by daller on 2007-01-19
> **mips said:**
> Do you want to open the laptop ? Might be wrtten on the chip.

The wireless NIC is placed in an easy accessible slot, AFAIK!

Opening the laptop is far better than booting Windows :lolflag:

---

### Post by mips on 2007-01-20
> **daller said:**
> The wireless NIC is placed in an easy accessible slot, AFAIK!


Ok, if it is underneath a trap door like mine then go for it. Only problem might be that the chipset is covered by RF shielding but have a look anyway. Write down all labels, PCB & chip labels numbers while you got it open, check both sides.

---

### Post by daller on 2007-01-20
> **mips said:**
> Ok, if it is underneath a trap door like mine then go for it. Only problem might be that the chipset is covered by RF shielding but have a look anyway. Write down all labels, PCB & chip labels numbers while you got it open, check both sides.

My soldering iron removed the shielding! :guitar: (**EDIT: The NIC still works!**)

It a Marvell 88W8335 chipset

Searching google seems like I have to go use ndiswrapper...:mad:

---

### Post by mips on 2007-01-20
The other option would be to go out and buy a Ralink or Intel one, theay are relatively cheap. I got a Intel mini-PCI (laptop) one for about 20euros.

---

