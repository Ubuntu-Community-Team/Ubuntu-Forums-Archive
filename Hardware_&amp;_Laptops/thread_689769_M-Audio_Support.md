---
title: "M-Audio Support?"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by lord_loafer on 2008-02-06
[SIZE="4"][SIZE="3"][COLOR="DimGray"][FONT="Century Gothic"]Hello all....

Firstly, i'd like to just say how great I think this forum is and although i'm very competent with PC's in general, i've not really used Linux much until the last few months. WIthout these forums, I can safely say that i'd be going back to Windows with my tail between my legs! I'm glad I stuck with it though as I now can honestly say i'm NEVER going back to Windows again!

Right.. onto the question.....

I have on board sound working fine, but also have a PCI M-audio Delta Audiophile 24/96 i'd LOVE to get working - I understand it uses something called an ICE1712 (or similar) driver, but have no idea how to configure it and get it working.. this is pretty much my only problem on Ubuntu now, so an idiots guide would be very welcome.

Thanks in advance!
Mark[/FONT][/COLOR][/SIZE][/SIZE]

:-\"

---

### Post by tgalati4 on 2008-02-06
>sudo apt-get install envy24control

>envy24control

---

### Post by lord_loafer on 2008-02-07
[FONT="Century Gothic"][SIZE="2"]Thank you very much for your swift reply, I now have envy24control install and when I run 'envy24control' I get a message that no ICE1712 cards are present...

Can you (or anyone else) please be so kind as to help me further?

Thanks again!

Best regards
Mark

:KS[/SIZE][/FONT]

---

### Post by Yellow Pasque on 2008-02-07
Use OSS4 for M-Audio cards. I have an M-Audio Revolution that works great with OSS4. See the link in my sig.

---

### Post by tgalati4 on 2008-02-07
Post the output of:

>lspci -vv

and

>lsmod

and

>cat /proc/interrupts

Finally:

>sudo modprobe snd-ice1712

>lsmod

If the above works then put *snd-ice1712* at the bottom of the file /etc/modules.  Reboot.  One of the few times you really do need to reboot in Linux.

---

### Post by lord_loafer on 2008-02-07
[FONT="Century Gothic"][SIZE="2"]Thanks again to all the help you guys are giving me.... i'm getting there....

I did what TEMUJIN suggested to do with OSS4 and the mixer seems ok etc, but still no sound... no errors or anything, but just no sound.... one thing I will note is that I did have sound with my onboard rubbish, but i've now disabled that. (although I understand that was using ALSA anyway?)

One thing I would also note is that in the Sound preferences section in preferences, although it says sound playback etc is on 'autodetect' there is only ALSA listed and when clicking test I get an error.

I'm getting closer though I think, as going on ossinfo shows:

-------------------------------------------------------------------------------------------
Version info: OSS 4.0 (b1013/200802012055) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (LOADED)

Number of audio devices:        7
Number of audio engines:        7
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: envy240 M Audio Audiophile 2496 interrupts=420270 (420270)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: M Audio Audiophile 2496 (Mixer 0 of device object 1)

Audio devices
M Audio Audiophile 2496 out1/2    /dev/oss/envy240/pcm0  (device index 0)
M Audio Audiophile 2496 S/PDIF out   /dev/oss/envy240/spdout  (device index 1)
M Audio Audiophile 2496 in1/2     /dev/oss/envy240/pcmin0  (device index 2)
M Audio Audiophile 2496 S/PDIF in   /dev/oss/envy240/spdin  (device index 3)
M Audio Audiophile 2496 input from mon. mixer   /dev/oss/envy240/mon  (device index 4)
M Audio Audiophile 2496 (all outputs)  /dev/oss/envy240/multich_out  (device index 5)
M Audio Audiophile 2496 (all inputs)  /dev/oss/envy240/multich_in  (device index 6)
-----------------------------------------------------------------------------------

Once again, thanks for everything, hope i'm not wasting anybodys time!

Best regards
Mark[/SIZE][/FONT]

---

### Post by lord_loafer on 2008-02-07
[COLOR="Red"]> **tgalati4 said:**
> Post the output of:

>lspci -vv[/COLOR]

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dde00000-ddefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ddf00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at bc00 [size=32]
        Region 4: I/O ports at 0600 [size=64]
        Region 5: I/O ports at 0700 [size=64]
        Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at dddfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 16
        Region 0: Memory at dddffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at b480 [size=8]
        Region 1: I/O ports at b400 [size=4]
        Region 2: I/O ports at b080 [size=8]
        Region 3: I/O ports at b000 [size=4]
        Region 4: I/O ports at ac00 [size=16]
        Region 5: Memory at dddfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at a880 [size=8]
        Region 1: I/O ports at a800 [size=4]
        Region 2: I/O ports at a480 [size=8]
        Region 3: I/O ports at a400 [size=4]
        Region 4: I/O ports at a080 [size=16]
        Region 5: Memory at dddfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at dddfb000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at a000 [size=8]
        Capabilities: <access denied>

00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at ddefc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at c800 [size=256]
        Expansion ROM at ddec0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2180
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        Region 5: I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 64
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at ec00 [size=32]
        Region 1: I/O ports at e880 [size=16]
        Region 2: I/O ports at e800 [size=16]
        Region 3: I/O ports at e480 [size=64]
        Capabilities: <access denied>


[COLOR="Red"]and

>lsmod[/COLOR]

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dde00000-ddefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ddf00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at bc00 [size=32]
        Region 4: I/O ports at 0600 [size=64]
        Region 5: I/O ports at 0700 [size=64]
        Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at dddfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 16
        Region 0: Memory at dddffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at b480 [size=8]
        Region 1: I/O ports at b400 [size=4]
        Region 2: I/O ports at b080 [size=8]
        Region 3: I/O ports at b000 [size=4]
        Region 4: I/O ports at ac00 [size=16]
        Region 5: Memory at dddfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at a880 [size=8]
        Region 1: I/O ports at a800 [size=4]
        Region 2: I/O ports at a480 [size=8]
        Region 3: I/O ports at a400 [size=4]
        Region 4: I/O ports at a080 [size=16]
        Region 5: Memory at dddfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at dddfb000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at a000 [size=8]
        Capabilities: <access denied>

00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at ddefc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at c800 [size=256]
        Expansion ROM at ddec0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2180
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        Region 5: I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 64
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at ec00 [size=32]
        Region 1: I/O ports at e880 [size=16]
        Region 2: I/O ports at e800 [size=16]
        Region 3: I/O ports at e480 [size=64]
        Capabilities: <access denied>

mb@LOADED:~$ lsmod
Module                  Size  Used by
nls_cp437               6784  0 
nls_utf8                3072  1 
cifs                  237428  1 
xt_limit                3584  8 
xt_tcpudp               4224  29 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
binfmt_misc            12936  1 
af_packet              24840  2 
ipv6                  273892  14 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vmix                   14132  2 
ossusb                 56072  2 
ich                    20464  2 
envy24                139516  6 
osscore               565940  4 vmix,ossusb,ich,envy24
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
video                  18060  0 
button                  8976  0 
battery                11012  0 
lp                     12580  0 
analog                 13344  0 
nvidia               6221648  34 
xpad                    9988  0 
agpgart                35016  1 nvidia
serio_raw               8068  0 
gameport               16776  1 analog
pcspkr                  4224  0 
sky2                   46852  0 
i2c_nforce2             7040  0 
parport_pc             37412  1 
psmouse                39952  0 
i2c_core               26112  2 nvidia,i2c_nforce2
parport                37448  3 ppdev,lp,parport_pc
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
k8temp                  6656  0 
evdev                  11136  4 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  7 
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sata_nv                20612  4 
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
floppy                 60004  0 
ohci_hcd               22916  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
forcedeth              51592  0 
ehci_hcd               36492  0 
usbcore               138632  6 ossusb,xpad,usbhid,ohci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor


[COLOR="Red"]and

>cat /proc/interrupts
[/COLOR]

           CPU0       CPU1       
  0:        154          0   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  6:          0          3   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          0          3   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          0          4   IO-APIC-edge      i8042
 14:        128       7433   IO-APIC-edge      ide0
 15:        149       7437   IO-APIC-edge      ide1
 16:          0        397   IO-APIC-fasteoi   ehci_hcd:usb1, sata_nv
 17:       4466     449684   IO-APIC-fasteoi   eth0
 18:        385      28159   IO-APIC-fasteoi   ohci_hcd:usb2
 19:        130      16443   IO-APIC-fasteoi   sata_nv
 20:        956      83947   IO-APIC-fasteoi   eth1, nvidia
 21:       3894     667505   IO-APIC-fasteoi   envy240
NMI:          0          0 
LOC:     188324     179387 
ERR:          1
MIS:          0

[COLOR="Red"]Finally:

>sudo modprobe snd-ice1712[/COLOR]

FATAL: Module snd_ice1712 not found.

[COLOR="Red"]>

If the above works then put *snd-ice1712* at the bottom of the file /etc/modules.  Reboot.  One of the few times you really do need to reboot in Linux.[/COLOR]

I'm very sorry about the length of this, but hope it helps!

Best regards
Mark

PS - Thanks once again!
:)

--------------------------------------------------------------

---

### Post by tgalati4 on 2008-02-07
Well, the kernel (I assume you are running Gutsy Gibbon) detects your hardware:

04:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
Latency: 64
Interrupt: pin A routed to IRQ 21
Region 0: I/O ports at ec00 [size=32]
Region 1: I/O ports at e880 [size=16]
Region 2: I/O ports at e800 [size=16]
Region 3: I/O ports at e480 [size=64]
Capabilities: <access denied>


And it's using Interrupt #21, which is not shared by any other device.

21: 3894 667505 IO-APIC-fasteoi envy240

BUT, you don't have snd-ice1712 driver.  I have it on my system and it shows up in lsmod (I'm using Linux Mint 4 XFCE--based on Gutsy).  I don't have an Audiophile card, I have an M-Audio Delta 66 card which uses the same envy24 sound chip.

It's a mystery.  You should at least try to find the driver and load it, so it will work under ALSA.  That way you will get system sounds and multiple devices to access the sound card.

Post the output of:

>locate ice1712

It should look like:

tgalati4@minty5:~$ locate ice1712
/lib/modules/2.6.22-14-generic/kernel/sound/pci/ice1712
/lib/modules/2.6.22-14-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/usr/src/linux-headers-2.6.22-14-generic/include/config/snd/ice1712.h
/usr/src/linux-headers-2.6.22-14/sound/pci/ice1712
/usr/src/linux-headers-2.6.22-14/sound/pci/ice1712/Makefile

A possible work around:  Turn off your on-board sound in BIOS during your next boot and see if the Audiophile card gets picked up properly.

---

### Post by seawright on 2008-02-08
If you still have oss4 loaded run:
osstest
Listen if there is any sound from loudspeakers and check printout for errors.

Don't worry if modules whose names begin with "snd" will not load, they are not needed with oss4.

Kind regards,
Clive

---

### Post by lord_loafer on 2008-02-08
[SIZE="2"][FONT="Century Gothic"]For Tgalati4:

This is my output:
[/FONT][/SIZE]
[SIZE="2"][COLOR="Red"]/usr/src/linux-headers-2.6.22-14/sound/pci/ice1712
/usr/src/linux-headers-2.6.22-14/sound/pci/ice1712/Makefile
/usr/src/linux-headers-2.6.22-14-generic/include/config/snd/ice1712.h[/COLOR][/SIZE]

[SIZE="2"][FONT="Century Gothic"]For the output of osstest:[/FONT][/SIZE]

[SIZE="2"][COLOR="Red"]Sound subsystem and version: OSS 4.0 (b1013/200802012055) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007

*** Scanning sound adapter #-1 ***
/dev/oss/envy240/pcm0 (audio engine 0): M Audio Audiophile 2496 out1/2
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 29858.00 Hz (-37.80%)> 
/dev/oss/envy240/spdout (audio engine 1): M Audio Audiophile 2496 S/PDIF out 
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47994.00 Hz (-0.01%)> 
/dev/oss/envy240/pcmin0 (audio engine 2): M Audio Audiophile 2496 in1/2
- Skipping input only device
/dev/oss/envy240/spdin (audio engine 3): M Audio Audiophile 2496 S/PDIF in 
- Skipping input only device
/dev/oss/envy240/mon (audio engine 4): M Audio Audiophile 2496 input from mon. mixer 
- Skipping input only device
/dev/oss/envy240/multich_out (audio engine 5): M Audio Audiophile 2496 (all outputs)
- Skipping multi channel device
/dev/oss/envy240/multich_in (audio engine 6): M Audio Audiophile 2496 (all inputs)
- Skipping input only device

*** All tests completed OK ***[/COLOR][/SIZE]


[FONT="Century Gothic"][SIZE="2"]
Once again, thanks for any help.... I may have to reinstall the OS at some point, i've changed (and probably messed up so many things!).

Best regards
Mark

:KS[/SIZE][/FONT]

---

### Post by seawright on 2008-02-08
Output from osstest looks ok.
Did you hear any music being played from the loudspeakers while the test was taking place?

If not run oss**x**mix and check that output volume sliders are at maximum then try osstest again.

Kind regards,
Clive

---

### Post by lord_loafer on 2008-02-08
[FONT="Century Gothic"][SIZE="2"]Hello.... thanks for your help Seawright...

I have just reinstalled Ubuntu 7.10 and have started the OSS4 install from scratch and all seems to have gone well... I can even now run ossmix and see the VU meters moving, still no sound!

Output from OSSINFO:[/SIZE][/FONT]

[COLOR="Red"]Version info: OSS 4.0 (b1013/200802012055) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 (LOADED)

Number of audio devices:        7
Number of audio engines:        7
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: envy240 M Audio Audiophile 2496 interrupts=170489 (170489)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: M Audio Audiophile 2496 (Mixer 0 of device object 1)

Audio devices
M Audio Audiophile 2496 out1/2    /dev/oss/envy240/pcm0  (device index 0)
M Audio Audiophile 2496 S/PDIF out   /dev/oss/envy240/spdout  (device index 1)
M Audio Audiophile 2496 in1/2     /dev/oss/envy240/pcmin0  (device index 2)
M Audio Audiophile 2496 S/PDIF in   /dev/oss/envy240/spdin  (device index 3)
M Audio Audiophile 2496 input from mon. mixer   /dev/oss/envy240/mon  (device index 4)
M Audio Audiophile 2496 (all outputs)  /dev/oss/envy240/multich_out  (device index 5)
M Audio Audiophile 2496 (all inputs)  /dev/oss/envy240/multich_in  (device index 6)
[/COLOR]
[COLOR="Black"][SIZE="2"][FONT="Century Gothic"]
This seems a lot cleaner than before... I run OSSTEST as below, but still no sound!:

[/FONT][/SIZE][/COLOR]

[COLOR="Red"]Sound subsystem and version: OSS 4.0 (b1013/200802012055) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/envy240/pcm0 (audio engine 0): M Audio Audiophile 2496 out1/2
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 23422.00 Hz (-51.20%)> 
/dev/oss/envy240/spdout (audio engine 1): M Audio Audiophile 2496 S/PDIF out 
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47992.00 Hz (-0.02%)> 
/dev/oss/envy240/pcmin0 (audio engine 2): M Audio Audiophile 2496 in1/2
- Skipping input only device
/dev/oss/envy240/spdin (audio engine 3): M Audio Audiophile 2496 S/PDIF in 
- Skipping input only device
/dev/oss/envy240/mon (audio engine 4): M Audio Audiophile 2496 input from mon. mixer 
- Skipping input only device
/dev/oss/envy240/multich_out (audio engine 5): M Audio Audiophile 2496 (all outputs)
- Skipping multi channel device
/dev/oss/envy240/multich_in (audio engine 6): M Audio Audiophile 2496 (all inputs)
- Skipping input only device

*** All tests completed OK ***[/COLOR]

[SIZE="2"][FONT="Century Gothic"][COLOR="Black"]Please continue to help if you can, I feel i'm close! I'm loving Linux and am trying my best to fly the flag... this community is far and away the best i've seen so far as well.... thanks again!

Best regards
Mark[/COLOR][/FONT][/SIZE]

:guitar:

---

### Post by seawright on 2008-02-08
What type of pc do you have (laptop desktop)?
Are there any other sockets that you can plug headphones into to check if the sound can be heard from them?

Kind regards,
Clive

---

### Post by Yellow Pasque on 2008-02-08
EDIT: You should continue with seawright's suggestion before trying what I instruct below.

Hey lord_loafer, it's good to hear you're liking Linux. Maybe we should try having you build OSS4 from source now that M-Audio has open-sourced their drivers in the latest release of OSS4 (build 1013).

Try this:
```
sudo soundoff
sudo dpkg -P oss-linux
```
That should uninstall the .deb package
Then download the tar source and follow the install instructions. You seem fairly intelligent, so I think you'll be okay. Nevertheless, if you run into problems, let us know.

**lord_loafer: a forum tip: use [ code ][ /code ] instead of [ quote ][ /quote ] when you post your output. It would also be considerate if you could edit your posts to use code blocks so that the thread becomes more readable to future viewers. Thanks.**

---

### Post by lord_loafer on 2008-02-09
> **Temüjin said:**
> EDIT: You should continue with seawright's suggestion before trying what I instruct below.

Hey lord_loafer, it's good to hear you're liking Linux. Maybe we should try having you build OSS4 from source now that M-Audio has open-sourced their drivers in the latest release of OSS4 (build 1013).

Try this:
```
sudo soundoff
sudo dpkg -P oss-linux
```
That should uninstall the .deb package
Then download the tar source and follow the install instructions. You seem fairly intelligent, so I think you'll be okay. Nevertheless, if you run into problems, let us know.

**lord_loafer: a forum tip: use [ code ][ /code ] instead of [ quote ][ /quote ] when you post your output. It would also be considerate if you could edit your posts to use code blocks so that the thread becomes more readable to future viewers. Thanks.**

[SIZE="2"]Thanks again Seawright, no dice unfortunately. Temujin - is the above necessary? I'm not questioning your advice, it's just that I only just reinstalled the whole OS and successfully installed the OSS4 as far as I know. The sound, according to the mixer VU, is being produced and all tests seem ok. 

As I said before, i'm more than happy to try your suggestion, as I know you know a hell of a lot more than me about it! But I was hoping there would be something less severe meantime!

Thanks once again for everything I really do love the OS and will persevere!

Best regards
Mark[/SIZE]
:confused:

---

### Post by seawright on 2008-02-09
Mark,
You still do not say whether your pc is a desktop or laptop and I do not know whether
M Audio Audiophile 2496 is available in cardbus format.
Laptop sound can be problematic so I am assuming you have a desktop or tower pc and that the soundcard is pci. Please correct me if I am wrong with my assumptions.

Anyway at the moment I am puzzled as to why your system is not working as all the checks appear to be ok yet still no sound.

Perhaps Temüjin's idea to install from source would either work or give some better clues as to what is wrong.

If you have not installed any packages from source before, please be assured that it is not difficult and is much quicker than doing a complete re-installation. Just remember to purge the existing oss package, following Temüjin's instructions, before compiling a new one as although the package you are using is a .deb package it is not from an official Debian or Ubuntu repository and can cause problems if you try to uninstall or upgrade later.

KInd regards,
Clive

---

### Post by lord_loafer on 2008-02-09
> **seawright said:**
> Mark,
You still do not say whether your pc is a desktop or laptop and I do not know whether
M Audio Audiophile 2496 is available in cardbus format.
Laptop sound can be problematic so I am assuming you have a desktop or tower pc and that the soundcard is pci. Please correct me if I am wrong with my assumptions.

Anyway at the moment I am puzzled as to why your system is not working as all the checks appear to be ok yet still no sound.

Perhaps Temüjin's idea to install from source would either work or give some better clues as to what is wrong.

If you have not installed any packages from source before, please be assured that it is not difficult and is much quicker than doing a complete re-installation. Just remember to purge the existing oss package, following Temüjin's instructions, before compiling a new one as although the package you are using is a .deb package it is not from an official Debian or Ubuntu repository and can cause problems if you try to uninstall or upgrade later.

KInd regards,
Clive
[SIZE="2"]
Hello Clive,

Sorry for not replying earlier about Laptop or Desktop... it's a desktop machine I have. I will try the source thing then and let you guys know what happens.

Thanks once again, you've all been great. I can't believe that people still use Windows when such a great OS and community is available!

Best regards
Mark[/SIZE]
:)

---

### Post by lord_loafer on 2008-02-09
[SIZE="2"]Hello all...

RIght.... I did the source compile and install and all went well... but still no sound! :confused:

The mixer VU is moving and the sound seems to be activated etc, but still nothing!

One thing worth mentioning would be that in the 'preferences/sound' panel, pressing test on this brings the following error... even when set to default out OSS:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

Hope this has any clues?

Thanks again!

Best regards
Mark[/SIZE]

---

### Post by Yellow Pasque on 2008-02-09
Hmm. Sounds like a pemisssions problem. Can you run a few commands for me?
```
cd /dev/oss; ls -l
cat /etc/group | grep audio
```

---

### Post by lord_loafer on 2008-02-09
> **Temüjin said:**
> Hmm. Sounds like a pemisssions problem. Can you run a few commands for me?
```
cd /dev/oss; ls -l
cat /etc/group | grep audio
```

[SIZE="2"]
Hello again,

I've had another play and am determined to get this issue sorted! :lolflag:

First:

```
total 0
drwxr-xr-x 2 root root 200 2008-02-09 20:01 envy240
```

and:

```
audio:x:29:mb
```

Thanks very much for all your help, it's a frustrating one! :)

Best regards
Mark[/SIZE]

---

### Post by Yellow Pasque on 2008-02-09
OK, I assume mb is your user name? If not, add your user to the audio group.

Also, I screwed up the other command. Do this:
```
cd /dev/oss/envy240; ls -l
```

---

### Post by Yellow Pasque on 2008-02-09
Oh, also go to the System -> Preferences -> Sound and change everything to OSS on the first tab. ON the second tab, make sure ESD software mixing is **not** checked.

---

### Post by lord_loafer on 2008-02-09
Hello again,

What's your name by the way? (if you don't mind of course!) It's just nice to be able to talk with real names...

Here is the output of /dev/oss$ cd /dev/oss/envy240; ls -l :

total 0
crw-rw-rw- 1 root root 252,  2 2008-02-09 20:01 mix0
crw-rw-rw- 1 root root 252, 11 2008-02-09 20:01 mon
crw-rw-rw- 1 root root 252, 15 2008-02-09 20:01 multich_in
crw-rw-rw- 1 root root 252, 13 2008-02-09 20:01 multich_out
crw-rw-rw- 1 root root 252,  3 2008-02-09 20:01 pcm0
crw-rw-rw- 1 root root 252,  7 2008-02-09 20:01 pcmin0
crw-rw-rw- 1 root root 252,  9 2008-02-09 20:01 spdin
crw-rw-rw- 1 root root 252,  5 2008-02-09 20:01 spdout

I have mb as user and have now disabled esd mixing... :)

I hate to keep posting on here whining about no sound, but i'm glad this sort of thing exists!

Best regards
Mark

---

### Post by Yellow Pasque on 2008-02-09
You're still not getting sound with osstest?

---

### Post by lord_loafer on 2008-02-09
[ATTACH]59203[/ATTACH]

The mixer seems active etc, but no sound appears routed... no sound on osstest, but all seems well... I know the sound card is ok as it worked 100% in Windows. Bloody thing.... might end up with rubbish onboard sound again after putting you gents through all this if it doesn't work!

:confused:

Best regards
Mark

---

### Post by Yellow Pasque on 2008-02-09
Don't be quick to give up. If we can't get it working then we'll file a bug report with the OSS4 developers.
Are you sure your sound prefs look like this?:

---

### Post by lord_loafer on 2008-02-09
Hello,

Aha... well... I don't have a default mixer listed and cannot access one... you click on the drop down menu and it is blank!

[ATTACH]59206[/ATTACH]

Interesting....

I just wish I knew more about this OS .... i've been happily installing loads of lovely free software lately though... some of it is so good!

I'm not really giving up yet, this is the final piece of the puzzle, everything else is running great! If it wasn't for people such as you though, i'd have probably thrown the towel in by now!

Best regards
Mark

---

### Post by Yellow Pasque on 2008-02-09
Hmm, let's try this (remember to post with [ code ] blocks as it might be long:
```
cd /dev; ls -l
```

---

### Post by lord_loafer on 2008-02-09
Glad you're still with me! :)

```
total 0
crw-rw---- 1 root   root    189,   5 2008-02-09 20:01 1-6
crw-rw---- 1 root   root    189, 129 2008-02-09 20:01 2-1
crw-rw---- 1 root   root    189, 130 2008-02-09 20:01 2-2
crw-rw---- 1 root   root    189, 131 2008-02-09 20:01 2-4
crw-rw---- 1 root   root    189, 132 2008-02-09 20:01 2-5
drwxr-xr-x 3 root   root          60 2008-02-09 20:01 bus
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 cdrom -> hdc
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 cdrom1 -> hda
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 cdrw1 -> hda
crw------- 1 root   root      5,   1 2008-02-09 20:01 console
lrwxrwxrwx 1 root   root          11 2008-02-09 20:01 core -> /proc/kcore
drwxr-xr-x 6 root   root         120 2008-02-09 20:01 disk
lrwxrwxrwx 1 root   root          21 2008-02-09 20:01 dsp0 -> /dev/oss/envy240/pcm0
lrwxrwxrwx 1 root   root          23 2008-02-09 20:01 dsp1 -> /dev/oss/envy240/spdout
lrwxrwxrwx 1 root   root          23 2008-02-09 20:01 dsp2 -> /dev/oss/envy240/pcmin0
lrwxrwxrwx 1 root   root          22 2008-02-09 20:01 dsp3 -> /dev/oss/envy240/spdin
lrwxrwxrwx 1 root   root          20 2008-02-09 20:01 dsp4 -> /dev/oss/envy240/mon
lrwxrwxrwx 1 root   root          28 2008-02-09 20:01 dsp5 -> /dev/oss/envy240/multich_out
lrwxrwxrwx 1 root   root          27 2008-02-09 20:01 dsp6 -> /dev/oss/envy240/multich_in
lrwxrwxrwx 1 root   root          23 2008-02-09 20:01 dsp_ac3 -> /dev/oss/envy240/spdout
lrwxrwxrwx 1 root   root          21 2008-02-09 20:01 dsp_multich -> /dev/oss/envy240/pcm0
lrwxrwxrwx 1 root   root          23 2008-02-09 20:01 dsp_spdifout -> /dev/oss/envy240/spdout
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 dvd -> hdc
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 dvd1 -> hda
lrwxrwxrwx 1 root   root           3 2008-02-09 20:01 dvdrw1 -> hda
lrwxrwxrwx 1 root   root          13 2008-02-09 20:01 fd -> /proc/self/fd
crw-rw-rw- 1 root   root      1,   7 2008-02-09 20:01 full
crw-rw---- 1 root   fuse     10, 229 2008-02-09 20:01 fuse
brw-rw---- 1 root   cdrom     3,   0 2008-02-09 20:01 hda
brw-rw---- 1 root   cdrom    22,   0 2008-02-09 20:01 hdc
crw-rw---- 1 root   root     10, 228 2008-02-09 20:01 hpet
prw------- 1 root   root           0 2008-02-09 20:01 initctl
drwxr-xr-x 4 root   root         300 2008-02-09 20:01 input
crw-r----- 1 root   kmem      1,   2 2007-10-16 00:18 kmem
crw-rw---- 1 root   root      1,  11 2008-02-09 20:01 kmsg
srw-rw-rw- 1 root   root           0 2008-02-09 20:01 log
brw------- 1 root   root      7,   0 2007-10-16 00:18 loop0
crw-rw---- 1 root   lp        6,   0 2008-02-09 20:01 lp0
lrwxrwxrwx 1 root   root          13 2008-02-09 20:01 MAKEDEV -> /sbin/MAKEDEV
crw-r----- 1 root   kmem      1,   1 2008-02-09 20:01 mem
crw-rw-rw- 1 root   root    253,   1 2008-02-09 20:01 mixer
lrwxrwxrwx 1 root   root          21 2008-02-09 20:01 mixer0 -> /dev/oss/envy240/mix0
drwxr-xr-x 2 root   root          60 2007-10-16 00:18 net
crw-rw-rw- 1 root   root      1,   3 2007-10-16 00:18 null
crw-rw-rw- 1 root   root    195,   0 2008-02-09 20:01 nvidia0
crw-rw-rw- 1 root   root    195, 255 2008-02-09 20:01 nvidiactl
crw-rw---- 1 root   root      1,  12 2008-02-09 20:01 oldmem
drwxr-xr-x 3 root   root          60 2008-02-09 20:01 oss
crw-rw---- 1 lp     scanner  99,   0 2008-02-09 20:01 parport0
crw-r----- 1 root   kmem      1,   4 2008-02-09 20:01 port
crw------- 1 root   root    108,   0 2007-10-16 00:18 ppp
crw-rw---- 1 root   root     10,   1 2008-02-09 20:01 psaux
crw-rw-rw- 1 root   root      5,   2 2008-02-10 01:18 ptmx
drwxr-xr-x 2 root   root           0 2008-02-09 20:01 pts
crw-rw-rw- 1 root   tty       2, 176 2008-02-09 20:01 ptya0
crw-rw-rw- 1 root   tty       2, 177 2008-02-09 20:01 ptya1
crw-rw-rw- 1 root   tty       2, 178 2008-02-09 20:01 ptya2
crw-rw-rw- 1 root   tty       2, 179 2008-02-09 20:01 ptya3
crw-rw-rw- 1 root   tty       2, 180 2008-02-09 20:01 ptya4
crw-rw-rw- 1 root   tty       2, 181 2008-02-09 20:01 ptya5
crw-rw-rw- 1 root   tty       2, 182 2008-02-09 20:01 ptya6
crw-rw-rw- 1 root   tty       2, 183 2008-02-09 20:01 ptya7
crw-rw-rw- 1 root   tty       2, 184 2008-02-09 20:01 ptya8
crw-rw-rw- 1 root   tty       2, 185 2008-02-09 20:01 ptya9
crw-rw-rw- 1 root   tty       2, 186 2008-02-09 20:01 ptyaa
crw-rw-rw- 1 root   tty       2, 187 2008-02-09 20:01 ptyab
crw-rw-rw- 1 root   tty       2, 188 2008-02-09 20:01 ptyac
crw-rw-rw- 1 root   tty       2, 189 2008-02-09 20:01 ptyad
crw-rw-rw- 1 root   tty       2, 190 2008-02-09 20:01 ptyae
crw-rw-rw- 1 root   tty       2, 191 2008-02-09 20:01 ptyaf
crw-rw-rw- 1 root   tty       2, 192 2008-02-09 20:01 ptyb0
crw-rw-rw- 1 root   tty       2, 193 2008-02-09 20:01 ptyb1
crw-rw-rw- 1 root   tty       2, 194 2008-02-09 20:01 ptyb2
crw-rw-rw- 1 root   tty       2, 195 2008-02-09 20:01 ptyb3
crw-rw-rw- 1 root   tty       2, 196 2008-02-09 20:01 ptyb4
crw-rw-rw- 1 root   tty       2, 197 2008-02-09 20:01 ptyb5
crw-rw-rw- 1 root   tty       2, 198 2008-02-09 20:01 ptyb6
crw-rw-rw- 1 root   tty       2, 199 2008-02-09 20:01 ptyb7
crw-rw-rw- 1 root   tty       2, 200 2008-02-09 20:01 ptyb8
crw-rw-rw- 1 root   tty       2, 201 2008-02-09 20:01 ptyb9
crw-rw-rw- 1 root   tty       2, 202 2008-02-09 20:01 ptyba
crw-rw-rw- 1 root   tty       2, 203 2008-02-09 20:01 ptybb
crw-rw-rw- 1 root   tty       2, 204 2008-02-09 20:01 ptybc
crw-rw-rw- 1 root   tty       2, 205 2008-02-09 20:01 ptybd
crw-rw-rw- 1 root   tty       2, 206 2008-02-09 20:01 ptybe
crw-rw-rw- 1 root   tty       2, 207 2008-02-09 20:01 ptybf
crw-rw-rw- 1 root   tty       2, 208 2008-02-09 20:01 ptyc0
crw-rw-rw- 1 root   tty       2, 209 2008-02-09 20:01 ptyc1
crw-rw-rw- 1 root   tty       2, 210 2008-02-09 20:01 ptyc2
crw-rw-rw- 1 root   tty       2, 211 2008-02-09 20:01 ptyc3
crw-rw-rw- 1 root   tty       2, 212 2008-02-09 20:01 ptyc4
crw-rw-rw- 1 root   tty       2, 213 2008-02-09 20:01 ptyc5
crw-rw-rw- 1 root   tty       2, 214 2008-02-09 20:01 ptyc6
crw-rw-rw- 1 root   tty       2, 215 2008-02-09 20:01 ptyc7
crw-rw-rw- 1 root   tty       2, 216 2008-02-09 20:01 ptyc8
crw-rw-rw- 1 root   tty       2, 217 2008-02-09 20:01 ptyc9
crw-rw-rw- 1 root   tty       2, 218 2008-02-09 20:01 ptyca
crw-rw-rw- 1 root   tty       2, 219 2008-02-09 20:01 ptycb
crw-rw-rw- 1 root   tty       2, 220 2008-02-09 20:01 ptycc
crw-rw-rw- 1 root   tty       2, 221 2008-02-09 20:01 ptycd
crw-rw-rw- 1 root   tty       2, 222 2008-02-09 20:01 ptyce
crw-rw-rw- 1 root   tty       2, 223 2008-02-09 20:01 ptycf
crw-rw-rw- 1 root   tty       2, 224 2008-02-09 20:01 ptyd0
crw-rw-rw- 1 root   tty       2, 225 2008-02-09 20:01 ptyd1
crw-rw-rw- 1 root   tty       2, 226 2008-02-09 20:01 ptyd2
crw-rw-rw- 1 root   tty       2, 227 2008-02-09 20:01 ptyd3
crw-rw-rw- 1 root   tty       2, 228 2008-02-09 20:01 ptyd4
crw-rw-rw- 1 root   tty       2, 229 2008-02-09 20:01 ptyd5
crw-rw-rw- 1 root   tty       2, 230 2008-02-09 20:01 ptyd6
crw-rw-rw- 1 root   tty       2, 231 2008-02-09 20:01 ptyd7
crw-rw-rw- 1 root   tty       2, 232 2008-02-09 20:01 ptyd8
crw-rw-rw- 1 root   tty       2, 233 2008-02-09 20:01 ptyd9
crw-rw-rw- 1 root   tty       2, 234 2008-02-09 20:01 ptyda
crw-rw-rw- 1 root   tty       2, 235 2008-02-09 20:01 ptydb
crw-rw-rw- 1 root   tty       2, 236 2008-02-09 20:01 ptydc
crw-rw-rw- 1 root   tty       2, 237 2008-02-09 20:01 ptydd
crw-rw-rw- 1 root   tty       2, 238 2008-02-09 20:01 ptyde
crw-rw-rw- 1 root   tty       2, 239 2008-02-09 20:01 ptydf
crw-rw-rw- 1 root   tty       2, 240 2008-02-09 20:01 ptye0
crw-rw-rw- 1 root   tty       2, 241 2008-02-09 20:01 ptye1
crw-rw-rw- 1 root   tty       2, 242 2008-02-09 20:01 ptye2
crw-rw-rw- 1 root   tty       2, 243 2008-02-09 20:01 ptye3
crw-rw-rw- 1 root   tty       2, 244 2008-02-09 20:01 ptye4
crw-rw-rw- 1 root   tty       2, 245 2008-02-09 20:01 ptye5
crw-rw-rw- 1 root   tty       2, 246 2008-02-09 20:01 ptye6
crw-rw-rw- 1 root   tty       2, 247 2008-02-09 20:01 ptye7
crw-rw-rw- 1 root   tty       2, 248 2008-02-09 20:01 ptye8
crw-rw-rw- 1 root   tty       2, 249 2008-02-09 20:01 ptye9
crw-rw-rw- 1 root   tty       2, 250 2008-02-09 20:01 ptyea
crw-rw-rw- 1 root   tty       2, 251 2008-02-09 20:01 ptyeb
crw-rw-rw- 1 root   tty       2, 252 2008-02-09 20:01 ptyec
crw-rw-rw- 1 root   tty       2, 253 2008-02-09 20:01 ptyed
crw-rw-rw- 1 root   tty       2, 254 2008-02-09 20:01 ptyee
crw-rw-rw- 1 root   tty       2, 255 2008-02-09 20:01 ptyef
crw-rw-rw- 1 root   tty       2,   0 2008-02-09 20:01 ptyp0
crw-rw-rw- 1 root   tty       2,   1 2008-02-09 20:01 ptyp1
crw-rw-rw- 1 root   tty       2,   2 2008-02-09 20:01 ptyp2
crw-rw-rw- 1 root   tty       2,   3 2008-02-09 20:01 ptyp3
crw-rw-rw- 1 root   tty       2,   4 2008-02-09 20:01 ptyp4
crw-rw-rw- 1 root   tty       2,   5 2008-02-09 20:01 ptyp5
crw-rw-rw- 1 root   tty       2,   6 2008-02-09 20:01 ptyp6
crw-rw-rw- 1 root   tty       2,   7 2008-02-09 20:01 ptyp7
crw-rw-rw- 1 root   tty       2,   8 2008-02-09 20:01 ptyp8
crw-rw-rw- 1 root   tty       2,   9 2008-02-09 20:01 ptyp9
crw-rw-rw- 1 root   tty       2,  10 2008-02-09 20:01 ptypa
crw-rw-rw- 1 root   tty       2,  11 2008-02-09 20:01 ptypb
crw-rw-rw- 1 root   tty       2,  12 2008-02-09 20:01 ptypc
crw-rw-rw- 1 root   tty       2,  13 2008-02-09 20:01 ptypd
crw-rw-rw- 1 root   tty       2,  14 2008-02-09 20:01 ptype
crw-rw-rw- 1 root   tty       2,  15 2008-02-09 20:01 ptypf
crw-rw-rw- 1 root   tty       2,  16 2008-02-09 20:01 ptyq0
crw-rw-rw- 1 root   tty       2,  17 2008-02-09 20:01 ptyq1
crw-rw-rw- 1 root   tty       2,  18 2008-02-09 20:01 ptyq2
crw-rw-rw- 1 root   tty       2,  19 2008-02-09 20:01 ptyq3
crw-rw-rw- 1 root   tty       2,  20 2008-02-09 20:01 ptyq4
crw-rw-rw- 1 root   tty       2,  21 2008-02-09 20:01 ptyq5
crw-rw-rw- 1 root   tty       2,  22 2008-02-09 20:01 ptyq6
crw-rw-rw- 1 root   tty       2,  23 2008-02-09 20:01 ptyq7
crw-rw-rw- 1 root   tty       2,  24 2008-02-09 20:01 ptyq8
crw-rw-rw- 1 root   tty       2,  25 2008-02-09 20:01 ptyq9
crw-rw-rw- 1 root   tty       2,  26 2008-02-09 20:01 ptyqa
crw-rw-rw- 1 root   tty       2,  27 2008-02-09 20:01 ptyqb
crw-rw-rw- 1 root   tty       2,  28 2008-02-09 20:01 ptyqc
crw-rw-rw- 1 root   tty       2,  29 2008-02-09 20:01 ptyqd
crw-rw-rw- 1 root   tty       2,  30 2008-02-09 20:01 ptyqe
crw-rw-rw- 1 root   tty       2,  31 2008-02-09 20:01 ptyqf
crw-rw-rw- 1 root   tty       2,  32 2008-02-09 20:01 ptyr0
crw-rw-rw- 1 root   tty       2,  33 2008-02-09 20:01 ptyr1
crw-rw-rw- 1 root   tty       2,  34 2008-02-09 20:01 ptyr2
crw-rw-rw- 1 root   tty       2,  35 2008-02-09 20:01 ptyr3
crw-rw-rw- 1 root   tty       2,  36 2008-02-09 20:01 ptyr4
crw-rw-rw- 1 root   tty       2,  37 2008-02-09 20:01 ptyr5
crw-rw-rw- 1 root   tty       2,  38 2008-02-09 20:01 ptyr6
crw-rw-rw- 1 root   tty       2,  39 2008-02-09 20:01 ptyr7
crw-rw-rw- 1 root   tty       2,  40 2008-02-09 20:01 ptyr8
crw-rw-rw- 1 root   tty       2,  41 2008-02-09 20:01 ptyr9
crw-rw-rw- 1 root   tty       2,  42 2008-02-09 20:01 ptyra
crw-rw-rw- 1 root   tty       2,  43 2008-02-09 20:01 ptyrb
crw-rw-rw- 1 root   tty       2,  44 2008-02-09 20:01 ptyrc
crw-rw-rw- 1 root   tty       2,  45 2008-02-09 20:01 ptyrd
crw-rw-rw- 1 root   tty       2,  46 2008-02-09 20:01 ptyre
crw-rw-rw- 1 root   tty       2,  47 2008-02-09 20:01 ptyrf
crw-rw-rw- 1 root   tty       2,  48 2008-02-09 20:01 ptys0
crw-rw-rw- 1 root   tty       2,  49 2008-02-09 20:01 ptys1
crw-rw-rw- 1 root   tty       2,  50 2008-02-09 20:01 ptys2
crw-rw-rw- 1 root   tty       2,  51 2008-02-09 20:01 ptys3
crw-rw-rw- 1 root   tty       2,  52 2008-02-09 20:01 ptys4
crw-rw-rw- 1 root   tty       2,  53 2008-02-09 20:01 ptys5
crw-rw-rw- 1 root   tty       2,  54 2008-02-09 20:01 ptys6
crw-rw-rw- 1 root   tty       2,  55 2008-02-09 20:01 ptys7
crw-rw-rw- 1 root   tty       2,  56 2008-02-09 20:01 ptys8
crw-rw-rw- 1 root   tty       2,  57 2008-02-09 20:01 ptys9
crw-rw-rw- 1 root   tty       2,  58 2008-02-09 20:01 ptysa
crw-rw-rw- 1 root   tty       2,  59 2008-02-09 20:01 ptysb
crw-rw-rw- 1 root   tty       2,  60 2008-02-09 20:01 ptysc
crw-rw-rw- 1 root   tty       2,  61 2008-02-09 20:01 ptysd
crw-rw-rw- 1 root   tty       2,  62 2008-02-09 20:01 ptyse
crw-rw-rw- 1 root   tty       2,  63 2008-02-09 20:01 ptysf
crw-rw-rw- 1 root   tty       2,  64 2008-02-09 20:01 ptyt0
crw-rw-rw- 1 root   tty       2,  65 2008-02-09 20:01 ptyt1
crw-rw-rw- 1 root   tty       2,  66 2008-02-09 20:01 ptyt2
crw-rw-rw- 1 root   tty       2,  67 2008-02-09 20:01 ptyt3
crw-rw-rw- 1 root   tty       2,  68 2008-02-09 20:01 ptyt4
crw-rw-rw- 1 root   tty       2,  69 2008-02-09 20:01 ptyt5
crw-rw-rw- 1 root   tty       2,  70 2008-02-09 20:01 ptyt6
crw-rw-rw- 1 root   tty       2,  71 2008-02-09 20:01 ptyt7
crw-rw-rw- 1 root   tty       2,  72 2008-02-09 20:01 ptyt8
crw-rw-rw- 1 root   tty       2,  73 2008-02-09 20:01 ptyt9
crw-rw-rw- 1 root   tty       2,  74 2008-02-09 20:01 ptyta
crw-rw-rw- 1 root   tty       2,  75 2008-02-09 20:01 ptytb
crw-rw-rw- 1 root   tty       2,  76 2008-02-09 20:01 ptytc
crw-rw-rw- 1 root   tty       2,  77 2008-02-09 20:01 ptytd
crw-rw-rw- 1 root   tty       2,  78 2008-02-09 20:01 ptyte
crw-rw-rw- 1 root   tty       2,  79 2008-02-09 20:01 ptytf
crw-rw-rw- 1 root   tty       2,  80 2008-02-09 20:01 ptyu0
crw-rw-rw- 1 root   tty       2,  81 2008-02-09 20:01 ptyu1
crw-rw-rw- 1 root   tty       2,  82 2008-02-09 20:01 ptyu2
crw-rw-rw- 1 root   tty       2,  83 2008-02-09 20:01 ptyu3
crw-rw-rw- 1 root   tty       2,  84 2008-02-09 20:01 ptyu4
crw-rw-rw- 1 root   tty       2,  85 2008-02-09 20:01 ptyu5
crw-rw-rw- 1 root   tty       2,  86 2008-02-09 20:01 ptyu6
crw-rw-rw- 1 root   tty       2,  87 2008-02-09 20:01 ptyu7
crw-rw-rw- 1 root   tty       2,  88 2008-02-09 20:01 ptyu8
crw-rw-rw- 1 root   tty       2,  89 2008-02-09 20:01 ptyu9
crw-rw-rw- 1 root   tty       2,  90 2008-02-09 20:01 ptyua
crw-rw-rw- 1 root   tty       2,  91 2008-02-09 20:01 ptyub
crw-rw-rw- 1 root   tty       2,  92 2008-02-09 20:01 ptyuc
crw-rw-rw- 1 root   tty       2,  93 2008-02-09 20:01 ptyud
crw-rw-rw- 1 root   tty       2,  94 2008-02-09 20:01 ptyue
crw-rw-rw- 1 root   tty       2,  95 2008-02-09 20:01 ptyuf
crw-rw-rw- 1 root   tty       2,  96 2008-02-09 20:01 ptyv0
crw-rw-rw- 1 root   tty       2,  97 2008-02-09 20:01 ptyv1
crw-rw-rw- 1 root   tty       2,  98 2008-02-09 20:01 ptyv2
crw-rw-rw- 1 root   tty       2,  99 2008-02-09 20:01 ptyv3
crw-rw-rw- 1 root   tty       2, 100 2008-02-09 20:01 ptyv4
crw-rw-rw- 1 root   tty       2, 101 2008-02-09 20:01 ptyv5
crw-rw-rw- 1 root   tty       2, 102 2008-02-09 20:01 ptyv6
crw-rw-rw- 1 root   tty       2, 103 2008-02-09 20:01 ptyv7
crw-rw-rw- 1 root   tty       2, 104 2008-02-09 20:01 ptyv8
crw-rw-rw- 1 root   tty       2, 105 2008-02-09 20:01 ptyv9
crw-rw-rw- 1 root   tty       2, 106 2008-02-09 20:01 ptyva
crw-rw-rw- 1 root   tty       2, 107 2008-02-09 20:01 ptyvb
crw-rw-rw- 1 root   tty       2, 108 2008-02-09 20:01 ptyvc
crw-rw-rw- 1 root   tty       2, 109 2008-02-09 20:01 ptyvd
crw-rw-rw- 1 root   tty       2, 110 2008-02-09 20:01 ptyve
crw-rw-rw- 1 root   tty       2, 111 2008-02-09 20:01 ptyvf
crw-rw-rw- 1 root   tty       2, 112 2008-02-09 20:01 ptyw0
crw-rw-rw- 1 root   tty       2, 113 2008-02-09 20:01 ptyw1
crw-rw-rw- 1 root   tty       2, 114 2008-02-09 20:01 ptyw2
crw-rw-rw- 1 root   tty       2, 115 2008-02-09 20:01 ptyw3
crw-rw-rw- 1 root   tty       2, 116 2008-02-09 20:01 ptyw4
crw-rw-rw- 1 root   tty       2, 117 2008-02-09 20:01 ptyw5
crw-rw-rw- 1 root   tty       2, 118 2008-02-09 20:01 ptyw6
crw-rw-rw- 1 root   tty       2, 119 2008-02-09 20:01 ptyw7
crw-rw-rw- 1 root   tty       2, 120 2008-02-09 20:01 ptyw8
crw-rw-rw- 1 root   tty       2, 121 2008-02-09 20:01 ptyw9
crw-rw-rw- 1 root   tty       2, 122 2008-02-09 20:01 ptywa
crw-rw-rw- 1 root   tty       2, 123 2008-02-09 20:01 ptywb
crw-rw-rw- 1 root   tty       2, 124 2008-02-09 20:01 ptywc
crw-rw-rw- 1 root   tty       2, 125 2008-02-09 20:01 ptywd
crw-rw-rw- 1 root   tty       2, 126 2008-02-09 20:01 ptywe
crw-rw-rw- 1 root   tty       2, 127 2008-02-09 20:01 ptywf
crw-rw-rw- 1 root   tty       2, 128 2008-02-09 20:01 ptyx0
crw-rw-rw- 1 root   tty       2, 129 2008-02-09 20:01 ptyx1
crw-rw-rw- 1 root   tty       2, 130 2008-02-09 20:01 ptyx2
crw-rw-rw- 1 root   tty       2, 131 2008-02-09 20:01 ptyx3
crw-rw-rw- 1 root   tty       2, 132 2008-02-09 20:01 ptyx4
crw-rw-rw- 1 root   tty       2, 133 2008-02-09 20:01 ptyx5
crw-rw-rw- 1 root   tty       2, 134 2008-02-09 20:01 ptyx6
crw-rw-rw- 1 root   tty       2, 135 2008-02-09 20:01 ptyx7
crw-rw-rw- 1 root   tty       2, 136 2008-02-09 20:01 ptyx8
crw-rw-rw- 1 root   tty       2, 137 2008-02-09 20:01 ptyx9
crw-rw-rw- 1 root   tty       2, 138 2008-02-09 20:01 ptyxa
crw-rw-rw- 1 root   tty       2, 139 2008-02-09 20:01 ptyxb
crw-rw-rw- 1 root   tty       2, 140 2008-02-09 20:01 ptyxc
crw-rw-rw- 1 root   tty       2, 141 2008-02-09 20:01 ptyxd
crw-rw-rw- 1 root   tty       2, 142 2008-02-09 20:01 ptyxe
crw-rw-rw- 1 root   tty       2, 143 2008-02-09 20:01 ptyxf
crw-rw-rw- 1 root   tty       2, 144 2008-02-09 20:01 ptyy0
crw-rw-rw- 1 root   tty       2, 145 2008-02-09 20:01 ptyy1
crw-rw-rw- 1 root   tty       2, 146 2008-02-09 20:01 ptyy2
crw-rw-rw- 1 root   tty       2, 147 2008-02-09 20:01 ptyy3
crw-rw-rw- 1 root   tty       2, 148 2008-02-09 20:01 ptyy4
crw-rw-rw- 1 root   tty       2, 149 2008-02-09 20:01 ptyy5
crw-rw-rw- 1 root   tty       2, 150 2008-02-09 20:01 ptyy6
crw-rw-rw- 1 root   tty       2, 151 2008-02-09 20:01 ptyy7
crw-rw-rw- 1 root   tty       2, 152 2008-02-09 20:01 ptyy8
crw-rw-rw- 1 root   tty       2, 153 2008-02-09 20:01 ptyy9
crw-rw-rw- 1 root   tty       2, 154 2008-02-09 20:01 ptyya
crw-rw-rw- 1 root   tty       2, 155 2008-02-09 20:01 ptyyb
crw-rw-rw- 1 root   tty       2, 156 2008-02-09 20:01 ptyyc
crw-rw-rw- 1 root   tty       2, 157 2008-02-09 20:01 ptyyd
crw-rw-rw- 1 root   tty       2, 158 2008-02-09 20:01 ptyye
crw-rw-rw- 1 root   tty       2, 159 2008-02-09 20:01 ptyyf
crw-rw-rw- 1 root   tty       2, 160 2008-02-09 20:01 ptyz0
crw-rw-rw- 1 root   tty       2, 161 2008-02-09 20:01 ptyz1
crw-rw-rw- 1 root   tty       2, 162 2008-02-09 20:01 ptyz2
crw-rw-rw- 1 root   tty       2, 163 2008-02-09 20:01 ptyz3
crw-rw-rw- 1 root   tty       2, 164 2008-02-09 20:01 ptyz4
crw-rw-rw- 1 root   tty       2, 165 2008-02-09 20:01 ptyz5
crw-rw-rw- 1 root   tty       2, 166 2008-02-09 20:01 ptyz6
crw-rw-rw- 1 root   tty       2, 167 2008-02-09 20:01 ptyz7
crw-rw-rw- 1 root   tty       2, 168 2008-02-09 20:01 ptyz8
crw-rw-rw- 1 root   tty       2, 169 2008-02-09 20:01 ptyz9
crw-rw-rw- 1 root   tty       2, 170 2008-02-09 20:01 ptyza
crw-rw-rw- 1 root   tty       2, 171 2008-02-09 20:01 ptyzb
crw-rw-rw- 1 root   tty       2, 172 2008-02-09 20:01 ptyzc
crw-rw-rw- 1 root   tty       2, 173 2008-02-09 20:01 ptyzd
crw-rw-rw- 1 root   tty       2, 174 2008-02-09 20:01 ptyze
crw-rw-rw- 1 root   tty       2, 175 2008-02-09 20:01 ptyzf
brw-rw---- 1 root   disk      1,   0 2008-02-09 20:01 ram0
brw-rw---- 1 root   disk      1,   1 2008-02-09 20:01 ram1
brw-rw---- 1 root   disk      1,  10 2008-02-09 20:01 ram10
brw-rw---- 1 root   disk      1,  11 2008-02-09 20:01 ram11
brw-rw---- 1 root   disk      1,  12 2008-02-09 20:01 ram12
brw-rw---- 1 root   disk      1,  13 2008-02-09 20:01 ram13
brw-rw---- 1 root   disk      1,  14 2008-02-09 20:01 ram14
brw-rw---- 1 root   disk      1,  15 2008-02-09 20:01 ram15
brw-rw---- 1 root   disk      1,   2 2008-02-09 20:01 ram2
brw-rw---- 1 root   disk      1,   3 2008-02-09 20:01 ram3
brw-rw---- 1 root   disk      1,   4 2008-02-09 20:01 ram4
brw-rw---- 1 root   disk      1,   5 2008-02-09 20:01 ram5
brw-rw---- 1 root   disk      1,   6 2008-02-09 20:01 ram6
brw-rw---- 1 root   disk      1,   7 2008-02-09 20:01 ram7
brw-rw---- 1 root   disk      1,   8 2008-02-09 20:01 ram8
brw-rw---- 1 root   disk      1,   9 2008-02-09 20:01 ram9
crw-rw-rw- 1 root   root      1,   8 2008-02-09 20:01 random
crw-rw---- 1 root   audio    10, 135 2008-02-09 20:01 rtc
brw-rw---- 1 root   disk      8,   0 2008-02-09 20:01 sda
brw-rw---- 1 root   disk      8,   1 2008-02-09 20:01 sda1
brw-rw---- 1 root   disk      8,   2 2008-02-09 20:01 sda2
brw-rw---- 1 root   disk      8,   5 2008-02-09 20:01 sda5
brw-rw---- 1 root   disk      8,  16 2008-02-09 20:01 sdb
brw-rw---- 1 root   disk      8,  18 2008-02-09 20:01 sdb2
brw-rw---- 1 root   disk      8,  32 2008-02-09 20:01 sdc
brw-rw---- 1 root   disk      8,  33 2008-02-09 20:01 sdc1
crw-rw---- 1 root   root     21,   0 2008-02-09 20:01 sg0
crw-rw---- 1 root   root     21,   1 2008-02-09 20:01 sg1
crw-rw---- 1 root   root     21,   2 2008-02-09 20:01 sg2
drwxrwxrwt 2 root   root          40 2008-02-09 20:01 shm
crw-rw---- 1 root   root     10, 231 2008-02-09 20:01 snapshot
crw-rw-rw- 1 root   root    253,   0 2008-02-09 20:01 sndstat
lrwxrwxrwx 1 root   root          15 2008-02-09 20:01 stderr -> /proc/self/fd/2
lrwxrwxrwx 1 root   root          15 2008-02-09 20:01 stdin -> /proc/self/fd/0
lrwxrwxrwx 1 root   root          15 2008-02-09 20:01 stdout -> /proc/self/fd/1
crw-rw-rw- 1 root   root      5,   0 2008-02-10 00:19 tty
crw-rw---- 1 root   root      4,   0 2008-02-09 20:01 tty0
crw------- 1 root   root      4,   1 2008-02-09 20:01 tty1
crw-rw---- 1 root   root      4,  10 2008-02-09 20:01 tty10
crw-rw---- 1 root   root      4,  11 2008-02-09 20:01 tty11
crw-rw---- 1 root   root      4,  12 2008-02-09 20:01 tty12
crw-rw---- 1 root   root      4,  13 2008-02-09 20:01 tty13
crw-rw---- 1 root   root      4,  14 2008-02-09 20:01 tty14
crw-rw---- 1 root   root      4,  15 2008-02-09 20:01 tty15
crw-rw---- 1 root   root      4,  16 2008-02-09 20:01 tty16
crw-rw---- 1 root   root      4,  17 2008-02-09 20:01 tty17
crw-rw---- 1 root   root      4,  18 2008-02-09 20:01 tty18
crw-rw---- 1 root   root      4,  19 2008-02-09 20:01 tty19
crw------- 1 root   root      4,   2 2008-02-09 20:01 tty2
crw-rw---- 1 root   root      4,  20 2008-02-09 20:01 tty20
crw-rw---- 1 root   root      4,  21 2008-02-09 20:01 tty21
crw-rw---- 1 root   root      4,  22 2008-02-09 20:01 tty22
crw-rw---- 1 root   root      4,  23 2008-02-09 20:01 tty23
crw-rw---- 1 root   root      4,  24 2008-02-09 20:01 tty24
crw-rw---- 1 root   root      4,  25 2008-02-09 20:01 tty25
crw-rw---- 1 root   root      4,  26 2008-02-09 20:01 tty26
crw-rw---- 1 root   root      4,  27 2008-02-09 20:01 tty27
crw-rw---- 1 root   root      4,  28 2008-02-09 20:01 tty28
crw-rw---- 1 root   root      4,  29 2008-02-09 20:01 tty29
crw------- 1 root   root      4,   3 2008-02-09 20:01 tty3
crw-rw---- 1 root   root      4,  30 2008-02-09 20:01 tty30
crw-rw---- 1 root   root      4,  31 2008-02-09 20:01 tty31
crw-rw---- 1 root   root      4,  32 2008-02-09 20:01 tty32
crw-rw---- 1 root   root      4,  33 2008-02-09 20:01 tty33
crw-rw---- 1 root   root      4,  34 2008-02-09 20:01 tty34
crw-rw---- 1 root   root      4,  35 2008-02-09 20:01 tty35
crw-rw---- 1 root   root      4,  36 2008-02-09 20:01 tty36
crw-rw---- 1 root   root      4,  37 2008-02-09 20:01 tty37
crw-rw---- 1 root   root      4,  38 2008-02-09 20:01 tty38
crw-rw---- 1 root   root      4,  39 2008-02-09 20:01 tty39
crw------- 1 root   root      4,   4 2008-02-09 20:01 tty4
crw-rw---- 1 root   root      4,  40 2008-02-09 20:01 tty40
crw-rw---- 1 root   root      4,  41 2008-02-09 20:01 tty41
crw-rw---- 1 root   root      4,  42 2008-02-09 20:01 tty42
crw-rw---- 1 root   root      4,  43 2008-02-09 20:01 tty43
crw-rw---- 1 root   root      4,  44 2008-02-09 20:01 tty44
crw-rw---- 1 root   root      4,  45 2008-02-09 20:01 tty45
crw-rw---- 1 root   root      4,  46 2008-02-09 20:01 tty46
crw-rw---- 1 root   root      4,  47 2008-02-09 20:01 tty47
crw-rw---- 1 root   root      4,  48 2008-02-09 20:01 tty48
crw-rw---- 1 root   root      4,  49 2008-02-09 20:01 tty49
crw------- 1 root   root      4,   5 2008-02-09 20:01 tty5
crw-rw---- 1 root   root      4,  50 2008-02-09 20:01 tty50
crw-rw---- 1 root   root      4,  51 2008-02-09 20:01 tty51
crw-rw---- 1 root   root      4,  52 2008-02-09 20:01 tty52
crw-rw---- 1 root   root      4,  53 2008-02-09 20:01 tty53
crw-rw---- 1 root   root      4,  54 2008-02-09 20:01 tty54
crw-rw---- 1 root   root      4,  55 2008-02-09 20:01 tty55
crw-rw---- 1 root   root      4,  56 2008-02-09 20:01 tty56
crw-rw---- 1 root   root      4,  57 2008-02-09 20:01 tty57
crw-rw---- 1 root   root      4,  58 2008-02-09 20:01 tty58
crw-rw---- 1 root   root      4,  59 2008-02-09 20:01 tty59
crw------- 1 root   root      4,   6 2008-02-09 20:01 tty6
crw-rw---- 1 root   root      4,  60 2008-02-09 20:01 tty60
crw-rw---- 1 root   root      4,  61 2008-02-09 20:01 tty61
crw-rw---- 1 root   root      4,  62 2008-02-09 20:01 tty62
crw-rw---- 1 root   root      4,  63 2008-02-09 20:01 tty63
crw-rw---- 1 root   root      4,   7 2008-02-09 20:01 tty7
crw-rw---- 1 root   root      4,   8 2008-02-09 20:01 tty8
crw-rw---- 1 root   root      4,   9 2008-02-09 20:01 tty9
crw-rw-rw- 1 root   tty       3, 176 2008-02-09 20:01 ttya0
crw-rw-rw- 1 root   tty       3, 177 2008-02-09 20:01 ttya1
crw-rw-rw- 1 root   tty       3, 178 2008-02-09 20:01 ttya2
crw-rw-rw- 1 root   tty       3, 179 2008-02-09 20:01 ttya3
crw-rw-rw- 1 root   tty       3, 180 2008-02-09 20:01 ttya4
crw-rw-rw- 1 root   tty       3, 181 2008-02-09 20:01 ttya5
crw-rw-rw- 1 root   tty       3, 182 2008-02-09 20:01 ttya6
crw-rw-rw- 1 root   tty       3, 183 2008-02-09 20:01 ttya7
crw-rw-rw- 1 root   tty       3, 184 2008-02-09 20:01 ttya8
crw-rw-rw- 1 root   tty       3, 185 2008-02-09 20:01 ttya9
crw-rw-rw- 1 root   tty       3, 186 2008-02-09 20:01 ttyaa
crw-rw-rw- 1 root   tty       3, 187 2008-02-09 20:01 ttyab
crw-rw-rw- 1 root   tty       3, 188 2008-02-09 20:01 ttyac
crw-rw-rw- 1 root   tty       3, 189 2008-02-09 20:01 ttyad
crw-rw-rw- 1 root   tty       3, 190 2008-02-09 20:01 ttyae
crw-rw-rw- 1 root   tty       3, 191 2008-02-09 20:01 ttyaf
crw-rw-rw- 1 root   tty       3, 192 2008-02-09 20:01 ttyb0
crw-rw-rw- 1 root   tty       3, 193 2008-02-09 20:01 ttyb1
crw-rw-rw- 1 root   tty       3, 194 2008-02-09 20:01 ttyb2
crw-rw-rw- 1 root   tty       3, 195 2008-02-09 20:01 ttyb3
crw-rw-rw- 1 root   tty       3, 196 2008-02-09 20:01 ttyb4
crw-rw-rw- 1 root   tty       3, 197 2008-02-09 20:01 ttyb5
crw-rw-rw- 1 root   tty       3, 198 2008-02-09 20:01 ttyb6
crw-rw-rw- 1 root   tty       3, 199 2008-02-09 20:01 ttyb7
crw-rw-rw- 1 root   tty       3, 200 2008-02-09 20:01 ttyb8
crw-rw-rw- 1 root   tty       3, 201 2008-02-09 20:01 ttyb9
crw-rw-rw- 1 root   tty       3, 202 2008-02-09 20:01 ttyba
crw-rw-rw- 1 root   tty       3, 203 2008-02-09 20:01 ttybb
crw-rw-rw- 1 root   tty       3, 204 2008-02-09 20:01 ttybc
crw-rw-rw- 1 root   tty       3, 205 2008-02-09 20:01 ttybd
crw-rw-rw- 1 root   tty       3, 206 2008-02-09 20:01 ttybe
crw-rw-rw- 1 root   tty       3, 207 2008-02-09 20:01 ttybf
crw-rw-rw- 1 root   tty       3, 208 2008-02-09 20:01 ttyc0
crw-rw-rw- 1 root   tty       3, 209 2008-02-09 20:01 ttyc1
crw-rw-rw- 1 root   tty       3, 210 2008-02-09 20:01 ttyc2
crw-rw-rw- 1 root   tty       3, 211 2008-02-09 20:01 ttyc3
crw-rw-rw- 1 root   tty       3, 212 2008-02-09 20:01 ttyc4
crw-rw-rw- 1 root   tty       3, 213 2008-02-09 20:01 ttyc5
crw-rw-rw- 1 root   tty       3, 214 2008-02-09 20:01 ttyc6
crw-rw-rw- 1 root   tty       3, 215 2008-02-09 20:01 ttyc7
crw-rw-rw- 1 root   tty       3, 216 2008-02-09 20:01 ttyc8
crw-rw-rw- 1 root   tty       3, 217 2008-02-09 20:01 ttyc9
crw-rw-rw- 1 root   tty       3, 218 2008-02-09 20:01 ttyca
crw-rw-rw- 1 root   tty       3, 219 2008-02-09 20:01 ttycb
crw-rw-rw- 1 root   tty       3, 220 2008-02-09 20:01 ttycc
crw-rw-rw- 1 root   tty       3, 221 2008-02-09 20:01 ttycd
crw-rw-rw- 1 root   tty       3, 222 2008-02-09 20:01 ttyce
crw-rw-rw- 1 root   tty       3, 223 2008-02-09 20:01 ttycf
crw-rw-rw- 1 root   tty       3, 224 2008-02-09 20:01 ttyd0
crw-rw-rw- 1 root   tty       3, 225 2008-02-09 20:01 ttyd1
crw-rw-rw- 1 root   tty       3, 226 2008-02-09 20:01 ttyd2
crw-rw-rw- 1 root   tty       3, 227 2008-02-09 20:01 ttyd3
crw-rw-rw- 1 root   tty       3, 228 2008-02-09 20:01 ttyd4
crw-rw-rw- 1 root   tty       3, 229 2008-02-09 20:01 ttyd5
crw-rw-rw- 1 root   tty       3, 230 2008-02-09 20:01 ttyd6
crw-rw-rw- 1 root   tty       3, 231 2008-02-09 20:01 ttyd7
crw-rw-rw- 1 root   tty       3, 232 2008-02-09 20:01 ttyd8
crw-rw-rw- 1 root   tty       3, 233 2008-02-09 20:01 ttyd9
crw-rw-rw- 1 root   tty       3, 234 2008-02-09 20:01 ttyda
crw-rw-rw- 1 root   tty       3, 235 2008-02-09 20:01 ttydb
crw-rw-rw- 1 root   tty       3, 236 2008-02-09 20:01 ttydc
crw-rw-rw- 1 root   tty       3, 237 2008-02-09 20:01 ttydd
crw-rw-rw- 1 root   tty       3, 238 2008-02-09 20:01 ttyde
crw-rw-rw- 1 root   tty       3, 239 2008-02-09 20:01 ttydf
crw-rw-rw- 1 root   tty       3, 240 2008-02-09 20:01 ttye0
crw-rw-rw- 1 root   tty       3, 241 2008-02-09 20:01 ttye1
crw-rw-rw- 1 root   tty       3, 242 2008-02-09 20:01 ttye2
crw-rw-rw- 1 root   tty       3, 243 2008-02-09 20:01 ttye3
crw-rw-rw- 1 root   tty       3, 244 2008-02-09 20:01 ttye4
crw-rw-rw- 1 root   tty       3, 245 2008-02-09 20:01 ttye5
crw-rw-rw- 1 root   tty       3, 246 2008-02-09 20:01 ttye6
crw-rw-rw- 1 root   tty       3, 247 2008-02-09 20:01 ttye7
crw-rw-rw- 1 root   tty       3, 248 2008-02-09 20:01 ttye8
crw-rw-rw- 1 root   tty       3, 249 2008-02-09 20:01 ttye9
crw-rw-rw- 1 root   tty       3, 250 2008-02-09 20:01 ttyea
crw-rw-rw- 1 root   tty       3, 251 2008-02-09 20:01 ttyeb
crw-rw-rw- 1 root   tty       3, 252 2008-02-09 20:01 ttyec
crw-rw-rw- 1 root   tty       3, 253 2008-02-09 20:01 ttyed
crw-rw-rw- 1 root   tty       3, 254 2008-02-09 20:01 ttyee
crw-rw-rw- 1 root   tty       3, 255 2008-02-09 20:01 ttyef
crw-rw-rw- 1 root   tty       3,   0 2008-02-09 20:01 ttyp0
crw-rw-rw- 1 root   tty       3,   1 2008-02-09 20:01 ttyp1
crw-rw-rw- 1 root   tty       3,   2 2008-02-09 20:01 ttyp2
crw-rw-rw- 1 root   tty       3,   3 2008-02-09 20:01 ttyp3
crw-rw-rw- 1 root   tty       3,   4 2008-02-09 20:01 ttyp4
crw-rw-rw- 1 root   tty       3,   5 2008-02-09 20:01 ttyp5
crw-rw-rw- 1 root   tty       3,   6 2008-02-09 20:01 ttyp6
crw-rw-rw- 1 root   tty       3,   7 2008-02-09 20:01 ttyp7
crw-rw-rw- 1 root   tty       3,   8 2008-02-09 20:01 ttyp8
crw-rw-rw- 1 root   tty       3,   9 2008-02-09 20:01 ttyp9
crw-rw-rw- 1 root   tty       3,  10 2008-02-09 20:01 ttypa
crw-rw-rw- 1 root   tty       3,  11 2008-02-09 20:01 ttypb
crw-rw-rw- 1 root   tty       3,  12 2008-02-09 20:01 ttypc
crw-rw-rw- 1 root   tty       3,  13 2008-02-09 20:01 ttypd
crw-rw-rw- 1 root   tty       3,  14 2008-02-09 20:01 ttype
crw-rw-rw- 1 root   tty       3,  15 2008-02-09 20:01 ttypf
crw-rw-rw- 1 root   tty       3,  16 2008-02-09 20:01 ttyq0
crw-rw-rw- 1 root   tty       3,  17 2008-02-09 20:01 ttyq1
crw-rw-rw- 1 root   tty       3,  18 2008-02-09 20:01 ttyq2
crw-rw-rw- 1 root   tty       3,  19 2008-02-09 20:01 ttyq3
crw-rw-rw- 1 root   tty       3,  20 2008-02-09 20:01 ttyq4
crw-rw-rw- 1 root   tty       3,  21 2008-02-09 20:01 ttyq5
crw-rw-rw- 1 root   tty       3,  22 2008-02-09 20:01 ttyq6
crw-rw-rw- 1 root   tty       3,  23 2008-02-09 20:01 ttyq7
crw-rw-rw- 1 root   tty       3,  24 2008-02-09 20:01 ttyq8
crw-rw-rw- 1 root   tty       3,  25 2008-02-09 20:01 ttyq9
crw-rw-rw- 1 root   tty       3,  26 2008-02-09 20:01 ttyqa
crw-rw-rw- 1 root   tty       3,  27 2008-02-09 20:01 ttyqb
crw-rw-rw- 1 root   tty       3,  28 2008-02-09 20:01 ttyqc
crw-rw-rw- 1 root   tty       3,  29 2008-02-09 20:01 ttyqd
crw-rw-rw- 1 root   tty       3,  30 2008-02-09 20:01 ttyqe
crw-rw-rw- 1 root   tty       3,  31 2008-02-09 20:01 ttyqf
crw-rw-rw- 1 root   tty       3,  32 2008-02-09 20:01 ttyr0
crw-rw-rw- 1 root   tty       3,  33 2008-02-09 20:01 ttyr1
crw-rw-rw- 1 root   tty       3,  34 2008-02-09 20:01 ttyr2
crw-rw-rw- 1 root   tty       3,  35 2008-02-09 20:01 ttyr3
crw-rw-rw- 1 root   tty       3,  36 2008-02-09 20:01 ttyr4
crw-rw-rw- 1 root   tty       3,  37 2008-02-09 20:01 ttyr5
crw-rw-rw- 1 root   tty       3,  38 2008-02-09 20:01 ttyr6
crw-rw-rw- 1 root   tty       3,  39 2008-02-09 20:01 ttyr7
crw-rw-rw- 1 root   tty       3,  40 2008-02-09 20:01 ttyr8
crw-rw-rw- 1 root   tty       3,  41 2008-02-09 20:01 ttyr9
crw-rw-rw- 1 root   tty       3,  42 2008-02-09 20:01 ttyra
crw-rw-rw- 1 root   tty       3,  43 2008-02-09 20:01 ttyrb
crw-rw-rw- 1 root   tty       3,  44 2008-02-09 20:01 ttyrc
crw-rw-rw- 1 root   tty       3,  45 2008-02-09 20:01 ttyrd
crw-rw-rw- 1 root   tty       3,  46 2008-02-09 20:01 ttyre
crw-rw-rw- 1 root   tty       3,  47 2008-02-09 20:01 ttyrf
crw-rw-rw- 1 root   tty       3,  48 2008-02-09 20:01 ttys0
crw-rw---- 1 root   dialout   4,  64 2008-02-09 20:01 ttyS0
crw-rw-rw- 1 root   tty       3,  49 2008-02-09 20:01 ttys1
crw-rw---- 1 root   dialout   4,  65 2008-02-09 20:01 ttyS1
crw-rw-rw- 1 root   tty       3,  50 2008-02-09 20:01 ttys2
crw-rw---- 1 root   dialout   4,  66 2008-02-09 20:01 ttyS2
crw-rw-rw- 1 root   tty       3,  51 2008-02-09 20:01 ttys3
crw-rw---- 1 root   dialout   4,  67 2008-02-09 20:01 ttyS3
crw-rw-rw- 1 root   tty       3,  52 2008-02-09 20:01 ttys4
crw-rw-rw- 1 root   tty       3,  53 2008-02-09 20:01 ttys5
crw-rw-rw- 1 root   tty       3,  54 2008-02-09 20:01 ttys6
crw-rw-rw- 1 root   tty       3,  55 2008-02-09 20:01 ttys7
crw-rw-rw- 1 root   tty       3,  56 2008-02-09 20:01 ttys8
crw-rw-rw- 1 root   tty       3,  57 2008-02-09 20:01 ttys9
crw-rw-rw- 1 root   tty       3,  58 2008-02-09 20:01 ttysa
crw-rw-rw- 1 root   tty       3,  59 2008-02-09 20:01 ttysb
crw-rw-rw- 1 root   tty       3,  60 2008-02-09 20:01 ttysc
crw-rw-rw- 1 root   tty       3,  61 2008-02-09 20:01 ttysd
crw-rw-rw- 1 root   tty       3,  62 2008-02-09 20:01 ttyse
crw-rw-rw- 1 root   tty       3,  63 2008-02-09 20:01 ttysf
crw-rw-rw- 1 root   tty       3,  64 2008-02-09 20:01 ttyt0
crw-rw-rw- 1 root   tty       3,  65 2008-02-09 20:01 ttyt1
crw-rw-rw- 1 root   tty       3,  66 2008-02-09 20:01 ttyt2
crw-rw-rw- 1 root   tty       3,  67 2008-02-09 20:01 ttyt3
crw-rw-rw- 1 root   tty       3,  68 2008-02-09 20:01 ttyt4
crw-rw-rw- 1 root   tty       3,  69 2008-02-09 20:01 ttyt5
crw-rw-rw- 1 root   tty       3,  70 2008-02-09 20:01 ttyt6
crw-rw-rw- 1 root   tty       3,  71 2008-02-09 20:01 ttyt7
crw-rw-rw- 1 root   tty       3,  72 2008-02-09 20:01 ttyt8
crw-rw-rw- 1 root   tty       3,  73 2008-02-09 20:01 ttyt9
crw-rw-rw- 1 root   tty       3,  74 2008-02-09 20:01 ttyta
crw-rw-rw- 1 root   tty       3,  75 2008-02-09 20:01 ttytb
crw-rw-rw- 1 root   tty       3,  76 2008-02-09 20:01 ttytc
crw-rw-rw- 1 root   tty       3,  77 2008-02-09 20:01 ttytd
crw-rw-rw- 1 root   tty       3,  78 2008-02-09 20:01 ttyte
crw-rw-rw- 1 root   tty       3,  79 2008-02-09 20:01 ttytf
crw-rw-rw- 1 root   tty       3,  80 2008-02-09 20:01 ttyu0
crw-rw-rw- 1 root   tty       3,  81 2008-02-09 20:01 ttyu1
crw-rw-rw- 1 root   tty       3,  82 2008-02-09 20:01 ttyu2
crw-rw-rw- 1 root   tty       3,  83 2008-02-09 20:01 ttyu3
crw-rw-rw- 1 root   tty       3,  84 2008-02-09 20:01 ttyu4
crw-rw-rw- 1 root   tty       3,  85 2008-02-09 20:01 ttyu5
crw-rw-rw- 1 root   tty       3,  86 2008-02-09 20:01 ttyu6
crw-rw-rw- 1 root   tty       3,  87 2008-02-09 20:01 ttyu7
crw-rw-rw- 1 root   tty       3,  88 2008-02-09 20:01 ttyu8
crw-rw-rw- 1 root   tty       3,  89 2008-02-09 20:01 ttyu9
crw-rw-rw- 1 root   tty       3,  90 2008-02-09 20:01 ttyua
crw-rw-rw- 1 root   tty       3,  91 2008-02-09 20:01 ttyub
crw-rw-rw- 1 root   tty       3,  92 2008-02-09 20:01 ttyuc
crw-rw-rw- 1 root   tty       3,  93 2008-02-09 20:01 ttyud
crw-rw-rw- 1 root   tty       3,  94 2008-02-09 20:01 ttyue
crw-rw-rw- 1 root   tty       3,  95 2008-02-09 20:01 ttyuf
crw-rw-rw- 1 root   tty       3,  96 2008-02-09 20:01 ttyv0
crw-rw-rw- 1 root   tty       3,  97 2008-02-09 20:01 ttyv1
crw-rw-rw- 1 root   tty       3,  98 2008-02-09 20:01 ttyv2
crw-rw-rw- 1 root   tty       3,  99 2008-02-09 20:01 ttyv3
crw-rw-rw- 1 root   tty       3, 100 2008-02-09 20:01 ttyv4
crw-rw-rw- 1 root   tty       3, 101 2008-02-09 20:01 ttyv5
crw-rw-rw- 1 root   tty       3, 102 2008-02-09 20:01 ttyv6
crw-rw-rw- 1 root   tty       3, 103 2008-02-09 20:01 ttyv7
crw-rw-rw- 1 root   tty       3, 104 2008-02-09 20:01 ttyv8
crw-rw-rw- 1 root   tty       3, 105 2008-02-09 20:01 ttyv9
crw-rw-rw- 1 root   tty       3, 106 2008-02-09 20:01 ttyva
crw-rw-rw- 1 root   tty       3, 107 2008-02-09 20:01 ttyvb
crw-rw-rw- 1 root   tty       3, 108 2008-02-09 20:01 ttyvc
crw-rw-rw- 1 root   tty       3, 109 2008-02-09 20:01 ttyvd
crw-rw-rw- 1 root   tty       3, 110 2008-02-09 20:01 ttyve
crw-rw-rw- 1 root   tty       3, 111 2008-02-09 20:01 ttyvf
crw-rw-rw- 1 root   tty       3, 112 2008-02-09 20:01 ttyw0
crw-rw-rw- 1 root   tty       3, 113 2008-02-09 20:01 ttyw1
crw-rw-rw- 1 root   tty       3, 114 2008-02-09 20:01 ttyw2
crw-rw-rw- 1 root   tty       3, 115 2008-02-09 20:01 ttyw3
crw-rw-rw- 1 root   tty       3, 116 2008-02-09 20:01 ttyw4
crw-rw-rw- 1 root   tty       3, 117 2008-02-09 20:01 ttyw5
crw-rw-rw- 1 root   tty       3, 118 2008-02-09 20:01 ttyw6
crw-rw-rw- 1 root   tty       3, 119 2008-02-09 20:01 ttyw7
crw-rw-rw- 1 root   tty       3, 120 2008-02-09 20:01 ttyw8
crw-rw-rw- 1 root   tty       3, 121 2008-02-09 20:01 ttyw9
crw-rw-rw- 1 root   tty       3, 122 2008-02-09 20:01 ttywa
crw-rw-rw- 1 root   tty       3, 123 2008-02-09 20:01 ttywb
crw-rw-rw- 1 root   tty       3, 124 2008-02-09 20:01 ttywc
crw-rw-rw- 1 root   tty       3, 125 2008-02-09 20:01 ttywd
crw-rw-rw- 1 root   tty       3, 126 2008-02-09 20:01 ttywe
crw-rw-rw- 1 root   tty       3, 127 2008-02-09 20:01 ttywf
crw-rw-rw- 1 root   tty       3, 128 2008-02-09 20:01 ttyx0
crw-rw-rw- 1 root   tty       3, 129 2008-02-09 20:01 ttyx1
crw-rw-rw- 1 root   tty       3, 130 2008-02-09 20:01 ttyx2
crw-rw-rw- 1 root   tty       3, 131 2008-02-09 20:01 ttyx3
crw-rw-rw- 1 root   tty       3, 132 2008-02-09 20:01 ttyx4
crw-rw-rw- 1 root   tty       3, 133 2008-02-09 20:01 ttyx5
crw-rw-rw- 1 root   tty       3, 134 2008-02-09 20:01 ttyx6
crw-rw-rw- 1 root   tty       3, 135 2008-02-09 20:01 ttyx7
crw-rw-rw- 1 root   tty       3, 136 2008-02-09 20:01 ttyx8
crw-rw-rw- 1 root   tty       3, 137 2008-02-09 20:01 ttyx9
crw-rw-rw- 1 root   tty       3, 138 2008-02-09 20:01 ttyxa
crw-rw-rw- 1 root   tty       3, 139 2008-02-09 20:01 ttyxb
crw-rw-rw- 1 root   tty       3, 140 2008-02-09 20:01 ttyxc
crw-rw-rw- 1 root   tty       3, 141 2008-02-09 20:01 ttyxd
crw-rw-rw- 1 root   tty       3, 142 2008-02-09 20:01 ttyxe
crw-rw-rw- 1 root   tty       3, 143 2008-02-09 20:01 ttyxf
crw-rw-rw- 1 root   tty       3, 144 2008-02-09 20:01 ttyy0
crw-rw-rw- 1 root   tty       3, 145 2008-02-09 20:01 ttyy1
crw-rw-rw- 1 root   tty       3, 146 2008-02-09 20:01 ttyy2
crw-rw-rw- 1 root   tty       3, 147 2008-02-09 20:01 ttyy3
crw-rw-rw- 1 root   tty       3, 148 2008-02-09 20:01 ttyy4
crw-rw-rw- 1 root   tty       3, 149 2008-02-09 20:01 ttyy5
crw-rw-rw- 1 root   tty       3, 150 2008-02-09 20:01 ttyy6
crw-rw-rw- 1 root   tty       3, 151 2008-02-09 20:01 ttyy7
crw-rw-rw- 1 root   tty       3, 152 2008-02-09 20:01 ttyy8
crw-rw-rw- 1 root   tty       3, 153 2008-02-09 20:01 ttyy9
crw-rw-rw- 1 root   tty       3, 154 2008-02-09 20:01 ttyya
crw-rw-rw- 1 root   tty       3, 155 2008-02-09 20:01 ttyyb
crw-rw-rw- 1 root   tty       3, 156 2008-02-09 20:01 ttyyc
crw-rw-rw- 1 root   tty       3, 157 2008-02-09 20:01 ttyyd
crw-rw-rw- 1 root   tty       3, 158 2008-02-09 20:01 ttyye
crw-rw-rw- 1 root   tty       3, 159 2008-02-09 20:01 ttyyf
crw-rw-rw- 1 root   tty       3, 160 2008-02-09 20:01 ttyz0
crw-rw-rw- 1 root   tty       3, 161 2008-02-09 20:01 ttyz1
crw-rw-rw- 1 root   tty       3, 162 2008-02-09 20:01 ttyz2
crw-rw-rw- 1 root   tty       3, 163 2008-02-09 20:01 ttyz3
crw-rw-rw- 1 root   tty       3, 164 2008-02-09 20:01 ttyz4
crw-rw-rw- 1 root   tty       3, 165 2008-02-09 20:01 ttyz5
crw-rw-rw- 1 root   tty       3, 166 2008-02-09 20:01 ttyz6
crw-rw-rw- 1 root   tty       3, 167 2008-02-09 20:01 ttyz7
crw-rw-rw- 1 root   tty       3, 168 2008-02-09 20:01 ttyz8
crw-rw-rw- 1 root   tty       3, 169 2008-02-09 20:01 ttyz9
crw-rw-rw- 1 root   tty       3, 170 2008-02-09 20:01 ttyza
crw-rw-rw- 1 root   tty       3, 171 2008-02-09 20:01 ttyzb
crw-rw-rw- 1 root   tty       3, 172 2008-02-09 20:01 ttyzc
crw-rw-rw- 1 root   tty       3, 173 2008-02-09 20:01 ttyzd
crw-rw-rw- 1 root   tty       3, 174 2008-02-09 20:01 ttyze
crw-rw-rw- 1 root   tty       3, 175 2008-02-09 20:01 ttyzf
crw-rw-rw- 1 root   root      1,   9 2008-02-09 20:01 urandom
drwxr-xr-x 2 root   root          60 2008-02-09 20:01 usb
crw-rw---- 1 root   root    189,   0 2008-02-09 20:01 usb1
crw-rw---- 1 root   root    189, 128 2008-02-09 20:01 usb2
crw-rw---- 1 root   root    254,   0 2008-02-09 20:01 usbdev1.1_ep00
crw-rw---- 1 root   root    254,   1 2008-02-09 20:01 usbdev1.1_ep81
crw-rw---- 1 root   root    254,   4 2008-02-09 20:01 usbdev1.6_ep00
crw-rw---- 1 root   root    254,   5 2008-02-09 20:01 usbdev1.6_ep81
crw-rw---- 1 root   root    254,   2 2008-02-09 20:01 usbdev2.1_ep00
crw-rw---- 1 root   root    254,   3 2008-02-09 20:01 usbdev2.1_ep81
crw-rw---- 1 root   root    254,   6 2008-02-09 20:01 usbdev2.2_ep00
crw-rw---- 1 root   root    254,   7 2008-02-09 20:01 usbdev2.2_ep81
crw-rw---- 1 root   root    254,   8 2008-02-09 20:01 usbdev2.3_ep00
crw-rw---- 1 root   root    254,   9 2008-02-09 20:01 usbdev2.3_ep81
crw-rw---- 1 root   root    254,  10 2008-02-09 20:01 usbdev2.4_ep00
crw-rw---- 1 root   root    254,  11 2008-02-09 20:01 usbdev2.4_ep81
crw-rw---- 1 root   root    254,  12 2008-02-09 20:01 usbdev2.4_ep82
crw-rw---- 1 root   root    254,  13 2008-02-09 20:01 usbdev2.5_ep00
crw-rw---- 1 root   root    254,  14 2008-02-09 20:01 usbdev2.5_ep81
crw-rw---- 1 root   root      7,   0 2008-02-09 20:01 vcs
crw-rw---- 1 root   root      7,   1 2008-02-09 20:01 vcs1
crw-rw---- 1 root   root      7,   2 2008-02-09 20:01 vcs2
crw-rw---- 1 root   root      7,   3 2008-02-09 20:01 vcs3
crw-rw---- 1 root   root      7,   4 2008-02-09 20:01 vcs4
crw-rw---- 1 root   root      7,   5 2008-02-09 20:01 vcs5
crw-rw---- 1 root   root      7,   6 2008-02-09 20:01 vcs6
crw-rw---- 1 root   root      7,   7 2008-02-10 01:13 vcs7
crw-rw---- 1 root   root      7,   8 2008-02-09 20:01 vcs8
crw-rw---- 1 root   root      7, 128 2008-02-09 20:01 vcsa
crw-rw---- 1 root   root      7, 129 2008-02-09 20:01 vcsa1
crw-rw---- 1 root   root      7, 130 2008-02-09 20:01 vcsa2
crw-rw---- 1 root   root      7, 131 2008-02-09 20:01 vcsa3
crw-rw---- 1 root   root      7, 132 2008-02-09 20:01 vcsa4
crw-rw---- 1 root   root      7, 133 2008-02-09 20:01 vcsa5
crw-rw---- 1 root   root      7, 134 2008-02-09 20:01 vcsa6
crw-rw---- 1 root   root      7, 135 2008-02-10 01:13 vcsa7
crw-rw---- 1 root   root      7, 136 2008-02-09 20:01 vcsa8
prw-r----- 1 syslog adm            0 2008-02-09 20:01 xconsole
crw-rw-rw- 1 root   root      1,   5 2008-02-09 20:01 zero

```

You're right about it being a long one!

:lolflag:

Best regards
Mark

---

### Post by Yellow Pasque on 2008-02-10
Ok, let's try disabling vmix and seeing if that helps. (Thank you for your patience here)
Run:
```
sudo soundoff
sudo gedit /usr/lib/oss/etc/installed_drivers
```
Remove the line that says "vmix #OSS Transparent Virtual Mixing Architecture"
If you don't plan on using USB audo devices, you can also remove the ossusb line too.
Then turn sound back on and test again:
```
sudo soundon
```

---

### Post by lord_loafer on 2008-02-10
> **Temüjin said:**
> Ok, let's try disabling vmix and seeing if that helps. (Thank you for your patience here)
Run:
```
sudo soundoff
sudo gedit /usr/lib/oss/etc/installed_drivers
```
Remove the line that says "vmix #OSS Transparent Virtual Mixing Architecture"
If you don't plan on using USB audo devices, you can also remove the ossusb line too.
Then turn sound back on and test again:
```
sudo soundon
```

You're thanking ME for MY Patience!!? Honestly, it's me that is thanking you for putting in so much effort to help me... thank you once again.

I'm still getting nothing i'm afraid... :(

It's so frustrating... seems as if something isn't routed right or something!

Best regards
Mark

PS - I seriously think that you guys on here keep Linux alive... without helpful people like you lot, I don't think Linux would be viable for a lot of people!

---

### Post by seawright on 2008-02-11
Do you know whether your hardware is definitely  working?
I know you said that the onboard sound worked so assuming you were using the same speakers I guess that gives them a clean bill of health but is your Audiophile 2496 ok?
Do you have a dual boot system so that you can check the sound card works using a different operating system?

It is still possible that there is a problem with the drivers but as this is proving so difficult (and it shouldn't) it may be worth proving the hardware before going any further.

Kind regards,
Clive

---

### Post by tgalati4 on 2008-02-11
You could try giving Dynebolic a spin.  It can be found at dynebolic.org.  It's a live CD that's designed for music production.  It has built-in envy24 drivers.  It uses an older kernel.  It's worth a shot to see if your card will even work with an older kernel without installing a different distro.

---

### Post by lord_loafer on 2008-02-11
Hello guys,

Thanks for all your help over the last few days, I really appreciate it!

However, I'm afraid to say i've now given up on it and have switched back to onboard sound! I tried everthing I could possibly find and also reinstalled my OS completely (twice!). Nevermind... i'll just buy a new card... any suggestions?

Sorry to give up, but it was causing me some damage to my mental health i'm sure!

Thanks to you all so much again,

Best regards
Mark

:KS

---

