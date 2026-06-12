---
title: "PC will not boot with HDD attached to  VT6421 SATA controller card"
date: 2011-03-26
forum: Hardware
---

### Post by ineedacold1 on 2011-03-26
Hello. I am a noob and having trouble with a SYBA VT6421 SATA / PATA combo controller card I added to a old HP 8670C pc (2000 bios).

With no HDD attached to the card, the pc boots fine. 

If I connect a extra known good PATA HDD, it goes through the PC bios, then to the SATA raid configure screen. I am not setting up  RAID. Boot Stops. At this point it should boot from the original HDD.

I tried this 
[http://kernelreloaded.blog385.com/in...ci-sata-howto/]("http://kernelreloaded.blog385.com/in...ci-sata-howto/")

Without the HDD attached to the SATA card. No luck.

Could it be IRQ issue?

If i need to, how do I change eth IRQ?

10.04LTS
Linux pavilion 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux


aes@pavilion:~$ lspci -vvv
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+ INTx-
	Latency: 0
	Region 0: Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: e0000000-e1cfffff
	Prefetchable memory behind bridge: e1f00000-e3ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 11)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at d800 [size=16]
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 05)
	Subsystem: First International Computer, Inc. Device 1234
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 11
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: i2c-viapro

00:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at d000 [size=16]
	Region 1: I/O ports at b800 [size=16]
	Region 2: I/O ports at b400 [size=16]
	Region 3: I/O ports at b000 [size=16]
	Region 4: I/O ports at a800 [size=32]
	Region 5: I/O ports at a400 [size=256]
	[virtual] Expansion ROM at 30100000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
	Subsystem: Hewlett-Packard Company Device 9207
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at a000 [size=256]
	Region 1: Memory at df800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too

HSF 56k PCI Modem
	Subsystem: Risq Modular Systems, Inc. Device 4311
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


00:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
	Subsystem: Intel Corporation Device 000b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 9400 [size=64]
	Region 2: Memory at dd800000 (32-bit, non-prefetchable) [size=1M]
	[virtual] Expansion ROM at 30000000 [disabled] [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100


Thank you for any help you can give me!

---

### Post by Hedgehog1 on 2011-03-26
ineedacold1,

The boot order can change as IDE drives and Sata drives are added/removed.

**Could you do this twice - once without the extra drive, and once with and post both results:**

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by ineedacold1 on 2011-03-26
Thanks. I am working on it.

Do you know why when I boot with HDD attached to the SATA controller using the LiveCD i boot to a command line?

---

### Post by kevind1234 on 2011-03-27
> **ineedacold1 said:**
> Hello. I am a noob and having trouble with a SYBA VT6421 SATA / PATA combo controller card I added to a old HP 8670C pc (2000 bios).

With no HDD attached to the card, the pc boots fine. 

If I connect a extra known good PATA HDD, it goes through the PC bios, then to the SATA raid configure screen. I am not setting up  RAID. Boot Stops. At this point it should boot from the original HDD.

I tried this 
[http://kernelreloaded.blog385.com/in...ci-sata-howto/]("http://kernelreloaded.blog385.com/in...ci-sata-howto/")

Without the HDD attached to the SATA card. No luck.

Could it be IRQ issue?

If i need to, how do I change eth IRQ?

10.04LTS
Linux pavilion 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux


aes@pavilion:~$ lspci -vvv
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+ INTx-
	Latency: 0
	Region 0: Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: e0000000-e1cfffff
	Prefetchable memory behind bridge: e1f00000-e3ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 11)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at d800 [size=16]
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 05)
	Subsystem: First International Computer, Inc. Device 1234
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 11
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: i2c-viapro

00:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at d000 [size=16]
	Region 1: I/O ports at b800 [size=16]
	Region 2: I/O ports at b400 [size=16]
	Region 3: I/O ports at b000 [size=16]
	Region 4: I/O ports at a800 [size=32]
	Region 5: I/O ports at a400 [size=256]
	[virtual] Expansion ROM at 30100000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
	Subsystem: Hewlett-Packard Company Device 9207
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at a000 [size=256]
	Region 1: Memory at df800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too

HSF 56k PCI Modem
	Subsystem: Risq Modular Systems, Inc. Device 4311
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


00:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
	Subsystem: Intel Corporation Device 000b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 9400 [size=64]
	Region 2: Memory at dd800000 (32-bit, non-prefetchable) [size=1M]
	[virtual] Expansion ROM at 30000000 [disabled] [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100


Thank you for any help you can give me!
Good Morning,
I am new to this forum and woud love to make a post however, I am not finding where to go to make a new post. Please send me some instruction how to make a post.
Thanks much

---

### Post by ineedacold1 on 2011-04-17
Hello The Hedge,
Thanks for the offer to help!

Here is the tow files.
RESULTS wo sata -> This does boot
RESULTS w sata -> This does not boot

Sda is the boot drive and the UUID is correct and set as sda1 in both reports.

I do see
set root='(hd1,msdos2)' in the report RESULTS wo sata
and
set root='(hd0,msdos1)' RESULTS w sata.

Is this the problem? This is in the "do not edit" grub.conf. I tried to reinstall grub2 but that did not work.

Any suggestion would be GREAT!!!!

Thanks

---

