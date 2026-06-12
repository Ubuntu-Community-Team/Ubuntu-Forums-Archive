---
title: "HELP: Configuring additional Serial PCI cards"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by shaileshjkumar on 2009-05-22
[COLOR="navy"]I have been trying to configure additional serial cards on a system with Ubuntu 9.04.

The two serials on the system are working OK and I have additional 2 X 4(PCI)= 8 Serials. So total of 10 serial ports. I run the following with output as:[/COLOR]

#cat /proc/tty/driver/serial
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3
4: uart:unknown port:00000000 irq:0
5: uart:unknown port:00000000 irq:0
6: uart:unknown port:00000000 irq:0
7: uart:unknown port:00000000 irq:0
8: uart:unknown port:00000000 irq:0
9: uart:unknown port:00000000 irq:0

[COLOR="navy"]When I try to connect to the additional serial using the tiny serial program "[http://dl.getdropbox.com/u/738335/serial.c.txt](http://dl.getdropbox.com/u/738335/serial.c.txt)" it gives me an I/O Error on the additional serials, but the two on board works fine.

When I do lspci the output is :[/COLOR]

# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0e.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:0e.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:0e.2 Parallel controller: Illegal Vendor ID Device 9865
00:0f.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:0f.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:0f.2 Parallel controller: Illegal Vendor ID Device 9865
00:10.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:10.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:10.2 Parallel controller: Illegal Vendor ID Device 9865
00:12.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:12.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller
00:12.2 Parallel controller: Illegal Vendor ID Device 9865
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

[COLOR="Navy"]It seems it did detect the PCI cards.

When I do "dmesg | grep -i tty"[/COLOR]

# dmesg | grep -i tty
[    0.004000] console [tty0] enabled
[    1.882372] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.882521] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.883339] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.883573] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.519307] Bluetooth: RFCOMM TTY layer initialized
[    2.519935] tty tty23: hash matches

[COLOR="navy"]How do I setup the Additional serials to work. Out of the 10 serials we have 6 occupied right now and 4 spare for future use. Out of the six, two are working which are on board, How to make the others work.[/COLOR]

[COLOR="navy"]I am not that familiar with the commands so a detailed help would be required. Thanx[/COLOR]:)

---

### Post by shaileshjkumar on 2009-05-22
[COLOR="navy"]I really need help with this..... anyone please.... is it possible or not....

I did lspci -vv
[/COLOR]
# lspci -vv
00:0e.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 8400 [size=8]
	Region 1: Memory at ed000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at ec800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:0e.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 18
	Region 0: I/O ports at 8000 [size=8]
	Region 1: Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at eb800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:0e.2 Parallel controller: Illegal Vendor ID Device 9865 (prog-if 03)
	Subsystem: Device a000:2000
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 0
	Region 0: I/O ports at 1000 [disabled] [size=8]
	Region 1: I/O ports at 1008 [disabled] [size=8]
	Region 2: Memory at 30000000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Region 4: Memory at 30001000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:0f.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 7800 [size=8]
	Region 1: Memory at eb000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at ea800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:0f.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 7400 [size=8]
	Region 1: Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at e9800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:0f.2 Parallel controller: Illegal Vendor ID Device 9865 (prog-if 03)
	Subsystem: Device a000:2000
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 0
	Region 0: I/O ports at 1010 [disabled] [size=8]
	Region 1: I/O ports at 1018 [disabled] [size=8]
	Region 2: Memory at 30002000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Region 4: Memory at 30003000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:10.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 7000 [size=8]
	Region 1: Memory at e9000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at e8800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:10.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 16
	Region 0: I/O ports at 6800 [size=8]
	Region 1: Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at e7800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:10.2 Parallel controller: Illegal Vendor ID Device 9865 (prog-if 03)
	Subsystem: Device a000:2000
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 0
	Region 0: I/O ports at 1020 [disabled] [size=8]
	Region 1: I/O ports at 1028 [disabled] [size=8]
	Region 2: Memory at 30004000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Region 4: Memory at 30005000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:12.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 6400 [size=8]
	Region 1: Memory at e7000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at e6800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:12.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 18
	Region 0: I/O ports at 6000 [size=8]
	Region 1: Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at e5800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:12.2 Parallel controller: Illegal Vendor ID Device 9865 (prog-if 03)
	Subsystem: Device a000:2000
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 0
	Region 0: I/O ports at 1030 [disabled] [size=8]
	Region 1: I/O ports at 1038 [disabled] [size=8]
	Region 2: Memory at 30006000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Region 4: Memory at 30007000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

[COLOR="Navy"]What do I have to do to solve this an get it to working?[/COLOR]

---

### Post by shaileshjkumar on 2009-05-25
Anyone please...I need help...

---

### Post by asavar on 2009-06-08
You need to create additional /dev/ttyS* nodes mannualy (as far as Linux supports only 4 by default) and map this nodes to physical ports using setserial command.

Read manuals on the controller's CD. On my CD manual for this procedure located at PCI_IO\9835_MIO\Linux folder. It is for 9835 controller, but procedure is the same.

---

### Post by shaileshjkumar on 2009-06-08
Thanks..... I was able to resolve this issue....

---

### Post by lordjoe on 2009-12-16
I never really figured out how to use setserial to enable the ports on my Netmos 9865 card.

I got it working with this patch: [http://patchwork.kernel.org/patch/65010/](http://patchwork.kernel.org/patch/65010/)

lspci -v shows:

05:04.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
  Subsystem: Device a000:1000
  Flags: bus master, medium devsel, latency 32, IRQ 16
  I/O ports at 1000 [size=8]
  Memory at f0500000 (32-bit, non-prefetchable) [size=4K]
  Memory at f0501000 (32-bit, non-prefetchable) [size=4K]
  Capabilities: [48] Power Management version 2
  Kernel driver in use: serial

05:04.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
  Subsystem: Device a000:1000
  Flags: bus master, medium devsel, latency 32, IRQ 18
  I/O ports at 1008 [size=8]
  Memory at f0502000 (32-bit, non-prefetchable) [size=4K]
  Memory at f0503000 (32-bit, non-prefetchable) [size=4K]
  Capabilities: [48] Power Management version 2
  Kernel driver in use: serial

05:04.2 Parallel controller: Illegal Vendor ID Device 9865 (prog-if 03 [IEEE1284])
  Subsystem: Device a000:2000
  Flags: medium devsel
  I/O ports at 1010 [disabled] [size=8]
  I/O ports at 1018 [disabled] [size=8]
  Memory at f0504000 (32-bit, non-prefetchable) [disabled] [size=4K]
  Memory at f0505000 (32-bit, non-prefetchable) [disabled] [size=4K]
  Capabilities: [48] Power Management version 2

---

