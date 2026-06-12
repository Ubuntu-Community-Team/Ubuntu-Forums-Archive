---
title: "Random hard lock"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by Cirdan7 on 2007-02-22
I keep getting random freezes while using Ubuntu Edgy.

System Specs:
Pentium 4 Dual-Core Hyper Threaded 3ghz
1 gig of ram
ATI Radeon 9700

What I have tried and failed:
Turned off Hyper-Threading in the bios.
Turned off Beryl.
Unplugged bad DVD Drive
Cannot ping the system when frozen.
CTRL-ALT-BACKSPACE doesn't do anything
CTRL-ALT-F1 doesn't do anything.
Windows runs fine on the same machine,slow, but it doesn't freeze.
Running it from the CD also freezes randomly.

The logs are clear for about 4-5 minuets before the crash happened, and nothing when the crash happened. Its not related to Firefox. I am using the default drivers that came with xorg.

---

### Post by gradedcheese on 2007-02-23
hmm, that's going to be interesting to troubleshoot.  Are there any other symptoms like more than the usual number of fans being on during the crash?  or the fans spinning faster than normal?  On a side note, I once saw a system that, with Windows, seemed to work but it would crash randomly in Linux.  As it turned out, the system had defective RAM (checked via memtest) and it just happened to be that the problem never came up in Windows (just by chance, really).  Replacing the RAM solved it.  If you happen to have extra RAM you can swap in, I'd at least give it a shot.

---

### Post by tgalati4 on 2007-02-23
Remove the Windows sticker.

Seriously, go into BIOS, turn CPU clock to 1.5 GHz, run for a while.  Linux will scream at 1.5 GHz with a P4.  Try reseating memory and run memtest overnight.

Look at dmesg and examine all of your error logs in /var/log.  All it takes is one error message to help troubleshoot.  I presume you have a massive heat sink on your cpu.  They do get toasty at 3 GHz.


Of course, your machine is running so fast under Ubuntu that you get caught in the Ballmer Reality Distortion Field and everything freezes including windows.

---

### Post by Cirdan7 on 2007-02-23
Yea..I have a heatsink + a fan on it. Temperature isn't a problem. One thing I did notice was in the logs it said hdc and hdd(dvd and cd drives respectively) were confused. I unplugged the hdc one because that one I know is going bad and those errors stopped, but it still froze. Also, I notice in the logs it said something like no IPv6 router found or something. I did run memtest while at school once and I didn't see anything indicating a memory error.

And my machine is quite slow...actually. takes forever for windows to boot up, and I don't have very many extra boot up processes at all. Maby it is a memory problem.

---

### Post by gradedcheese on 2007-02-23
Alright.  The IPv6 messages are fine, it's just not finding an IPv6 router (as they don't really exist in most places yet).  Just to be sure, please check all of your IDE/ATA cabling: master and slave drives are connected where they should be?  Drives are actually set to master or slave and not cable-select?  The latter sometimes causes interesting problems.

---

### Post by tgalati4 on 2007-02-23
You mentioned a failing hdc (DVD).  A failing drive (harddisk or DVD) will cause excessive interrupts while it tries to read media--slowing down the pci bus, yet not causing visible errors.  Because these storage devices are connected to the main data bus, any problems will cause the machine to slow down.  What looks like a freeze could simply be an interrupt storm caused by the bad disk.

I had a Promise ATA controller take a dump on me with similar strange symptons.  Once removed everything worked.

Good luck, we need you in the fight.  Grab an extra bandolier on the way out.

---

### Post by LilRayRay on 2007-03-12
I have what seems to be an identical problem.  I will be using linux and it will randomly freeze up COMPLETELY, ad as you have said, crtl+alt command do nothing.  The only thing left for me to do is to force my computer to shut down by holding the power button.  I think it has something to do with the processor.  In 6.06, it ran fine untill I enabled the second core of my Penitum D, and after this I began getting these crashes.  Now that edgy is smp, I get these crashes somewhat often.  Makes me ever so angry.

---

### Post by tgalati4 on 2007-03-13
Any results with declocking these SMP systems?

---

### Post by ender42 on 2007-03-14
I ran into a similar hard-lock, and no ping or anything, but someone suggested that I dust my machine, because the CPU was overheating - which was the issue.

You said that you know it's not overheating.... do you have a software monitor?  I know that somewhere, something does do something like that, but I don't know how to check it.  Which would've made diagnosing my problem much easier :D

---

### Post by mibs on 2007-03-14
Did you install anything or make any changes to the system just before you noticed this happening? I don't know if this has anything to do with it, but i recently installed cpudyn from synaptic, then ubuntu edgy would freeze and no commands would work. I booted into recovery mode and removed the package and I haven't had a problem since.

---

### Post by Cirdan7 on 2007-03-20
Well, I hope bumping is ok but I'm still getting the same problem. Something interesting I found when I ran sudo lspci -vvnn. More specifically at the end when it says something about BusMaster. I looked up BusMaster and its a IDE driver used only for windows 95 and is no longer supported. Could this be the problem, or is it even related in any way? And you cannot declock this processor.

> 
00:00.0 0600: 8086:2570 (rev 02)
        Subsystem: 8086:2570
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [e4] Vendor Specific Information
        Capabilities: [a0] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=2 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4

00:01.0 0604: 8086:2571 (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ff700000-ff7fffff
        Prefetchable memory behind bridge: e8000000-f7ffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-

00:03.0 0604: 8086:2573 (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff800000-ff8fffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1d.0 0c03: 8086:24d2 (rev 02)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 169
        Region 4: I/O ports at cc00 [size=32]

00:1d.1 0c03: 8086:24d4 (rev 02)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 177
        Region 4: I/O ports at d000 [size=32]

00:1d.2 0c03: 8086:24d7 (rev 02)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 185
        Region 4: I/O ports at d400 [size=32]

00:1d.3 0c03: 8086:24de (rev 02)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 169
        Region 4: I/O ports at d800 [size=32]

00:1d.7 0c03: 8086:24dd (rev 02) (prog-if 20)
        Subsystem: 8086:524c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 193
        Region 0: Memory at ffa00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port

00:1e.0 0604: 8086:244e (rev c2)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: ff900000-ff9fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 0601: 8086:24d0 (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 0101: 8086:24db (rev 02) (prog-if 8a)
        Subsystem: 8086:524c
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 185
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at ffa0 [size=16]
        Region 5: Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 0104: 8086:24df (rev 02) (prog-if 8f)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 185
        Region 0: I/O ports at ec00 [size=8]
        Region 1: I/O ports at e800 [size=4]
        Region 2: I/O ports at e400 [size=8]
        Region 3: I/O ports at e000 [size=4]
        Region 4: I/O ports at dc00 [size=16]

00:1f.3 0c05: 8086:24d3 (rev 02)
        Subsystem: 8086:524c
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 201
        Region 4: I/O ports at c800 [size=32]

00:1f.5 0401: 8086:24d5 (rev 02)
        Subsystem: 8086:a000
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 201
        Region 2: Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at ffa00800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 0300: 1002:4e45
        Subsystem: 1002:0002
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at a800 [size=256]
        Region 2: Memory at ff720000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff700000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
                Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=32 ArqSz=2 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.1 0380: 1002:4e65
        Subsystem: 1002:0003
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min), Cache Line Size: 64 bytes
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at ff730000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:01.0 0200: 8086:1019
        Subsystem: 8086:301f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (63750ns min), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at ff800000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at bc00 [size=32]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-

03:02.0 0c00: 104c:8020 (prog-if 10)
        Subsystem: 104c:8020
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at ff905000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at ff900000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

03:07.0 0c00: 11c1:5811 (rev 61) (prog-if 10)
        Subsystem: 8086:524c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (3000ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at ff904000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

---

### Post by tgalati4 on 2007-03-26
If the machine is on the network, enable sshd (sudo sshd) then login in from another machine (sshd user@hostname).  This will establish a terminal session between the machines.  Run your suspect machine until it freezes.  Check the remote terminal session to determine that the machine has frozen.  (Use w or top to verify)

I have had wonky video cards freeze which mimic a system freeze.  Only through a remote session or sometimes the capslock key will determine if your system is still functioning under the frozen exterior.

I'm surprised your BIOS does not have a way to turn down the clocking factor.  Most modern boards do.  

I think BusMaster under Linux refers to a device on the PCI bus that demands more attention, such as taking control of the bus if necessary.

The other thing to do is reseat all of the internal cards.  As the machine heats up, contact resistance can change causing pci bus problems.  These will lock a system hard.

Wouldn't hotpug for pci devices be interesting?

---

### Post by deja on 2007-04-20
I believe I have narrowed down my hard-lock problems to the CPU Frequency Manager in my Dell Inspiron 5150 (P4 3.2 HT) in Edgy. 

My computer has been now up for 25 hours, which is 24.5 hours longer than the average time I got between lockups.

---

### Post by mtwin2 on 2007-04-30
My system has been randomly freezing as well, my specs are:

OS: Ubuntu 7.04 Final Release
CPU: AMD Athlon 64 3500+
Motherboard: ASUS A8R-MVP
RAM: 1.5GB (3x512MB) - Corsair ValueSelect DDR400 / PC3200
Video: SAPPHIRE 100146L Radeon X1600XT 256MB GDDR3 (connected via DVI)

I'm using Beryl and the ATI fglrx driver, although these freezes happened before installing both of these things.  Here is the kernel log from the most recent freeze of my system which occurred a few minutes ago.  Any help would be greatly appreciated, also let me know if you need any other information.

```

Apr 29 11:17:15 mhayes-pc kernel: [36801.687184] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:17:15 mhayes-pc kernel: [36801.687191] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:17:15 mhayes-pc kernel: [36801.687194] ide: failed opcode was: unknown
Apr 29 11:17:15 mhayes-pc kernel: [36801.687558] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:17:15 mhayes-pc kernel: [36801.687562] end_request: I/O error, dev hdc, sector 1964
Apr 29 11:17:15 mhayes-pc kernel: [36801.687566] Buffer I/O error on device hdc, logical block 491
Apr 29 11:17:15 mhayes-pc kernel: [36801.687572] Buffer I/O error on device hdc, logical block 492
Apr 29 11:17:15 mhayes-pc kernel: [36801.687574] Buffer I/O error on device hdc, logical block 493
Apr 29 11:17:15 mhayes-pc kernel: [36801.687577] Buffer I/O error on device hdc, logical block 494
Apr 29 11:17:15 mhayes-pc kernel: [36801.687580] Buffer I/O error on device hdc, logical block 495
Apr 29 11:17:15 mhayes-pc kernel: [36801.687582] Buffer I/O error on device hdc, logical block 496
Apr 29 11:17:15 mhayes-pc kernel: [36801.687585] Buffer I/O error on device hdc, logical block 497
Apr 29 11:17:15 mhayes-pc kernel: [36801.687588] Buffer I/O error on device hdc, logical block 498
Apr 29 11:17:15 mhayes-pc kernel: [36801.687590] Buffer I/O error on device hdc, logical block 499
Apr 29 11:17:15 mhayes-pc kernel: [36801.687593] Buffer I/O error on device hdc, logical block 500
Apr 29 11:32:09 mhayes-pc kernel: [37694.156388] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:32:09 mhayes-pc kernel: [37694.156395] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:32:09 mhayes-pc kernel: [37694.156398] ide: failed opcode was: unknown
Apr 29 11:32:09 mhayes-pc kernel: [37694.156764] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:32:09 mhayes-pc kernel: [37694.156768] end_request: I/O error, dev hdc, sector 1964
Apr 29 11:32:09 mhayes-pc kernel: [37694.156772] printk: 37 messages suppressed.
Apr 29 11:32:09 mhayes-pc kernel: [37694.156774] Buffer I/O error on device hdc, logical block 491
Apr 29 11:32:09 mhayes-pc kernel: [37694.156780] Buffer I/O error on device hdc, logical block 492
Apr 29 11:32:09 mhayes-pc kernel: [37694.156783] Buffer I/O error on device hdc, logical block 493
Apr 29 11:32:09 mhayes-pc kernel: [37694.156785] Buffer I/O error on device hdc, logical block 494
Apr 29 11:32:09 mhayes-pc kernel: [37694.156788] Buffer I/O error on device hdc, logical block 495
Apr 29 11:32:09 mhayes-pc kernel: [37694.156790] Buffer I/O error on device hdc, logical block 496
Apr 29 11:32:09 mhayes-pc kernel: [37694.156793] Buffer I/O error on device hdc, logical block 497
Apr 29 11:32:09 mhayes-pc kernel: [37694.156796] Buffer I/O error on device hdc, logical block 498
Apr 29 11:32:09 mhayes-pc kernel: [37694.156799] Buffer I/O error on device hdc, logical block 499
Apr 29 11:32:09 mhayes-pc kernel: [37694.156801] Buffer I/O error on device hdc, logical block 500
Apr 29 11:32:09 mhayes-pc kernel: [37694.777945] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:32:09 mhayes-pc kernel: [37694.777952] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:32:09 mhayes-pc kernel: [37694.777955] ide: failed opcode was: unknown
Apr 29 11:32:09 mhayes-pc kernel: [37694.778320] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:32:09 mhayes-pc kernel: [37694.778324] end_request: I/O error, dev hdc, sector 304548
Apr 29 11:32:26 mhayes-pc kernel: [37711.718879] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:32:26 mhayes-pc kernel: [37711.718886] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:32:26 mhayes-pc kernel: [37711.718889] ide: failed opcode was: unknown
Apr 29 11:32:26 mhayes-pc kernel: [37711.719252] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:32:26 mhayes-pc kernel: [37711.719256] end_request: I/O error, dev hdc, sector 23044
Apr 29 11:32:26 mhayes-pc kernel: [37711.719259] printk: 38 messages suppressed.
Apr 29 11:32:26 mhayes-pc kernel: [37711.719261] Buffer I/O error on device hdc, logical block 5761
Apr 29 11:32:41 mhayes-pc kernel: [37726.758751] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:32:41 mhayes-pc kernel: [37726.758758] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:32:41 mhayes-pc kernel: [37726.758761] ide: failed opcode was: unknown
Apr 29 11:32:41 mhayes-pc kernel: [37726.759125] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:32:41 mhayes-pc kernel: [37726.759129] end_request: I/O error, dev hdc, sector 304548
Apr 29 11:32:41 mhayes-pc kernel: [37726.759133] Buffer I/O error on device hdc, logical block 76137
Apr 29 11:32:44 mhayes-pc kernel: [37729.176076] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:32:44 mhayes-pc kernel: [37729.176083] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:32:44 mhayes-pc kernel: [37729.176086] ide: failed opcode was: unknown
Apr 29 11:32:44 mhayes-pc kernel: [37729.176451] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:32:44 mhayes-pc kernel: [37729.176454] end_request: I/O error, dev hdc, sector 304548
Apr 29 11:32:44 mhayes-pc kernel: [37729.176459] Buffer I/O error on device hdc, logical block 76137
Apr 29 11:39:24 mhayes-pc kernel: [38128.935487] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:39:24 mhayes-pc kernel: [38128.935494] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:39:24 mhayes-pc kernel: [38128.935497] ide: failed opcode was: unknown
Apr 29 11:39:24 mhayes-pc kernel: [38128.935861] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:39:24 mhayes-pc kernel: [38128.935865] end_request: I/O error, dev hdc, sector 23044
Apr 29 11:39:24 mhayes-pc kernel: [38128.935869] Buffer I/O error on device hdc, logical block 5761
Apr 29 11:47:58 mhayes-pc kernel: [38642.443642] [fglrx] total      GART = 130023424
Apr 29 11:47:58 mhayes-pc kernel: [38642.443648] [fglrx] free       GART = 114032640
Apr 29 11:47:58 mhayes-pc kernel: [38642.443650] [fglrx] max single GART = 114032640
Apr 29 11:47:58 mhayes-pc kernel: [38642.443652] [fglrx] total      LFB  = 268304384
Apr 29 11:47:58 mhayes-pc kernel: [38642.443654] [fglrx] free       LFB  = 250089472
Apr 29 11:47:58 mhayes-pc kernel: [38642.443656] [fglrx] max single LFB  = 250089472
Apr 29 11:47:58 mhayes-pc kernel: [38642.443657] [fglrx] total      Inv  = 0
Apr 29 11:47:58 mhayes-pc kernel: [38642.443659] [fglrx] free       Inv  = 0
Apr 29 11:47:58 mhayes-pc kernel: [38642.443660] [fglrx] max single Inv  = 0
Apr 29 11:47:58 mhayes-pc kernel: [38642.443662] [fglrx] total      TIM  = 0
Apr 29 11:48:59 mhayes-pc kernel: [38703.949271] hdc: irq timeout: status=0xd0 { Busy }
Apr 29 11:48:59 mhayes-pc kernel: [38703.949276] ide: failed opcode was: unknown
Apr 29 11:49:17 mhayes-pc kernel: [38721.705896] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:17 mhayes-pc kernel: [38721.705903] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:17 mhayes-pc kernel: [38721.705906] ide: failed opcode was: unknown
Apr 29 11:49:17 mhayes-pc kernel: [38721.706271] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:17 mhayes-pc kernel: [38721.706274] end_request: I/O error, dev hdc, sector 1964
Apr 29 11:49:17 mhayes-pc kernel: [38721.706279] Buffer I/O error on device hdc, logical block 491
Apr 29 11:49:17 mhayes-pc kernel: [38721.706284] Buffer I/O error on device hdc, logical block 492
Apr 29 11:49:17 mhayes-pc kernel: [38721.706287] Buffer I/O error on device hdc, logical block 493
Apr 29 11:49:17 mhayes-pc kernel: [38721.706290] Buffer I/O error on device hdc, logical block 494
Apr 29 11:49:17 mhayes-pc kernel: [38721.706293] Buffer I/O error on device hdc, logical block 495
Apr 29 11:49:17 mhayes-pc kernel: [38721.706296] Buffer I/O error on device hdc, logical block 496
Apr 29 11:49:17 mhayes-pc kernel: [38721.706299] Buffer I/O error on device hdc, logical block 497
Apr 29 11:49:17 mhayes-pc kernel: [38721.706301] Buffer I/O error on device hdc, logical block 498
Apr 29 11:49:17 mhayes-pc kernel: [38721.706304] Buffer I/O error on device hdc, logical block 499
Apr 29 11:49:17 mhayes-pc kernel: [38721.706307] Buffer I/O error on device hdc, logical block 500
Apr 29 11:49:17 mhayes-pc kernel: [38722.004260] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:17 mhayes-pc kernel: [38722.004267] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:17 mhayes-pc kernel: [38722.004271] ide: failed opcode was: unknown
Apr 29 11:49:17 mhayes-pc kernel: [38722.004636] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:17 mhayes-pc kernel: [38722.004639] end_request: I/O error, dev hdc, sector 304544
Apr 29 11:49:17 mhayes-pc kernel: [38722.120079] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:17 mhayes-pc kernel: [38722.120084] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:17 mhayes-pc kernel: [38722.120087] ide: failed opcode was: unknown
Apr 29 11:49:17 mhayes-pc kernel: [38722.120446] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:17 mhayes-pc kernel: [38722.120449] end_request: I/O error, dev hdc, sector 304544
Apr 29 11:49:18 mhayes-pc kernel: [38722.316869] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38722.316876] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38722.316879] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38722.317244] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38722.317247] end_request: I/O error, dev hdc, sector 304552
Apr 29 11:49:18 mhayes-pc kernel: [38722.432515] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38722.432522] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38722.432525] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38722.432890] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38722.432894] end_request: I/O error, dev hdc, sector 304552
Apr 29 11:49:18 mhayes-pc kernel: [38722.629003] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38722.629010] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38722.629013] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38722.629375] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38722.629378] end_request: I/O error, dev hdc, sector 304560
Apr 29 11:49:18 mhayes-pc kernel: [38722.744478] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38722.744485] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38722.744488] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38722.744854] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38722.744857] end_request: I/O error, dev hdc, sector 304560
Apr 29 11:49:18 mhayes-pc kernel: [38722.940684] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38722.940691] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38722.940694] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38722.941059] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38722.941063] end_request: I/O error, dev hdc, sector 304568
Apr 29 11:49:18 mhayes-pc kernel: [38723.056224] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38723.056231] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38723.056234] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38723.056596] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38723.056600] end_request: I/O error, dev hdc, sector 304568
Apr 29 11:49:18 mhayes-pc kernel: [38723.178271] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:18 mhayes-pc kernel: [38723.178278] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:18 mhayes-pc kernel: [38723.178281] ide: failed opcode was: unknown
Apr 29 11:49:18 mhayes-pc kernel: [38723.178647] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:18 mhayes-pc kernel: [38723.178650] end_request: I/O error, dev hdc, sector 304576
Apr 29 11:49:19 mhayes-pc kernel: [38723.316954] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38723.316961] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38723.316964] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38723.317332] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38723.317335] end_request: I/O error, dev hdc, sector 304576
Apr 29 11:49:19 mhayes-pc kernel: [38723.524820] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38723.524827] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38723.524830] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38723.525193] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38723.525196] end_request: I/O error, dev hdc, sector 304584
Apr 29 11:49:19 mhayes-pc kernel: [38723.663286] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38723.663293] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38723.663296] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38723.663660] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38723.663663] end_request: I/O error, dev hdc, sector 304584
Apr 29 11:49:19 mhayes-pc kernel: [38723.870895] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38723.870902] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38723.870905] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38723.871268] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38723.871272] end_request: I/O error, dev hdc, sector 304588
Apr 29 11:49:19 mhayes-pc kernel: [38724.078374] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38724.078380] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38724.078383] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38724.078746] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38724.078749] end_request: I/O error, dev hdc, sector 304592
Apr 29 11:49:19 mhayes-pc kernel: [38724.205085] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:19 mhayes-pc kernel: [38724.205092] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:19 mhayes-pc kernel: [38724.205095] ide: failed opcode was: unknown
Apr 29 11:49:19 mhayes-pc kernel: [38724.205460] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:19 mhayes-pc kernel: [38724.205463] end_request: I/O error, dev hdc, sector 304592
Apr 29 11:49:20 mhayes-pc kernel: [38724.412267] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38724.412273] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38724.412276] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38724.412640] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38724.412643] end_request: I/O error, dev hdc, sector 304600
Apr 29 11:49:20 mhayes-pc kernel: [38724.538781] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38724.538786] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38724.538788] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38724.539147] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38724.539151] end_request: I/O error, dev hdc, sector 304600
Apr 29 11:49:20 mhayes-pc kernel: [38724.745923] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38724.745929] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38724.745932] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38724.746294] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38724.746298] end_request: I/O error, dev hdc, sector 304608
Apr 29 11:49:20 mhayes-pc kernel: [38724.872707] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38724.872714] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38724.872717] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38724.873083] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38724.873086] end_request: I/O error, dev hdc, sector 304608
Apr 29 11:49:20 mhayes-pc kernel: [38725.080090] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38725.080097] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38725.080100] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38725.080463] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38725.080467] end_request: I/O error, dev hdc, sector 304616
Apr 29 11:49:20 mhayes-pc kernel: [38725.206720] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:20 mhayes-pc kernel: [38725.206727] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:20 mhayes-pc kernel: [38725.206729] ide: failed opcode was: unknown
Apr 29 11:49:20 mhayes-pc kernel: [38725.207095] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:20 mhayes-pc kernel: [38725.207099] end_request: I/O error, dev hdc, sector 304616
Apr 29 11:49:21 mhayes-pc kernel: [38725.413772] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:21 mhayes-pc kernel: [38725.413779] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:21 mhayes-pc kernel: [38725.413782] ide: failed opcode was: unknown
Apr 29 11:49:21 mhayes-pc kernel: [38725.414145] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:21 mhayes-pc kernel: [38725.414148] end_request: I/O error, dev hdc, sector 304624
Apr 29 11:49:21 mhayes-pc kernel: [38725.540241] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:21 mhayes-pc kernel: [38725.540248] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:21 mhayes-pc kernel: [38725.540251] ide: failed opcode was: unknown
Apr 29 11:49:21 mhayes-pc kernel: [38725.540615] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:21 mhayes-pc kernel: [38725.540618] end_request: I/O error, dev hdc, sector 304624
Apr 29 11:49:21 mhayes-pc kernel: [38725.771292] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:21 mhayes-pc kernel: [38725.771299] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:21 mhayes-pc kernel: [38725.771302] ide: failed opcode was: unknown
Apr 29 11:49:21 mhayes-pc kernel: [38725.771667] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:21 mhayes-pc kernel: [38725.771671] end_request: I/O error, dev hdc, sector 304720
Apr 29 11:49:21 mhayes-pc kernel: [38725.977926] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:21 mhayes-pc kernel: [38725.977933] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:21 mhayes-pc kernel: [38725.977936] ide: failed opcode was: unknown
Apr 29 11:49:21 mhayes-pc kernel: [38725.978300] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:21 mhayes-pc kernel: [38725.978303] end_request: I/O error, dev hdc, sector 304724
Apr 29 11:49:21 mhayes-pc kernel: [38726.115607] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:21 mhayes-pc kernel: [38726.115614] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:21 mhayes-pc kernel: [38726.115617] ide: failed opcode was: unknown
Apr 29 11:49:21 mhayes-pc kernel: [38726.115979] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:21 mhayes-pc kernel: [38726.115983] end_request: I/O error, dev hdc, sector 304720
Apr 29 11:49:51 mhayes-pc kernel: [38756.144629] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:49:51 mhayes-pc kernel: [38756.144636] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:49:51 mhayes-pc kernel: [38756.144639] ide: failed opcode was: unknown
Apr 29 11:49:51 mhayes-pc kernel: [38756.145005] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:49:51 mhayes-pc kernel: [38756.145009] end_request: I/O error, dev hdc, sector 23044
Apr 29 11:49:51 mhayes-pc kernel: [38756.145012] printk: 85 messages suppressed.
Apr 29 11:49:51 mhayes-pc kernel: [38756.145015] Buffer I/O error on device hdc, logical block 5761
Apr 29 11:52:24 mhayes-pc kernel: [38908.911257] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Apr 29 11:52:24 mhayes-pc kernel: [38908.911264] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Apr 29 11:52:24 mhayes-pc kernel: [38908.911267] ide: failed opcode was: unknown
Apr 29 11:52:24 mhayes-pc kernel: [38908.911628] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
Apr 29 11:52:24 mhayes-pc kernel: [38908.911632] end_request: I/O error, dev hdc, sector 1960
Apr 29 11:52:24 mhayes-pc kernel: [38908.911636] Buffer I/O error on device hdc, logical block 245
Apr 29 11:52:24 mhayes-pc kernel: [38908.911640] Buffer I/O error on device hdc, logical block 246
Apr 29 11:52:24 mhayes-pc kernel: [38908.911643] Buffer I/O error on device hdc, logical block 247
Apr 29 11:52:24 mhayes-pc kernel: [38908.911645] Buffer I/O error on device hdc, logical block 248
Apr 29 11:52:24 mhayes-pc kernel: [38908.911648] Buffer I/O error on device hdc, logical block 249
Apr 29 11:52:24 mhayes-pc kernel: [38908.911651] Buffer I/O error on device hdc, logical block 250
Apr 29 11:52:24 mhayes-pc kernel: [38908.911653] Buffer I/O error on device hdc, logical block 251
Apr 29 11:52:24 mhayes-pc kernel: [38908.911656] Buffer I/O error on device hdc, logical block 252
Apr 29 11:52:24 mhayes-pc kernel: [38908.911658] Buffer I/O error on device hdc, logical block 253
Apr 29 11:52:24 mhayes-pc kernel: [38908.911661] Buffer I/O error on device hdc, logical block 254

```

---

### Post by bonzini on 2007-04-30
I had a lot of difficulties with lockups in Edgy and Feisty.  However, Feisty provided a clue that turned out to be a problem with a workaround, and now there's a bug report filed against it [https://bugs.launchpad.net/bugs/98999](https://bugs.launchpad.net/bugs/98999)

To make a long story short, try booting with the "noapic" option.

---

### Post by mtwin2 on 2007-04-30
I should also mention that I'm using these boot parameters:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ef8e4547-dcdd-4551-a7f4-fbc0162af1a8 ro quiet splash noapic force acpi no irq nosmp
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

