---
title: "Oxford 8 port PCIe Serial Card"
date: 2010-02-24
forum: Hardware
---

### Post by LawnDart471 on 2010-02-24
Hi there. 

I'm hoping someone has been through this. I've been all over the internet looking for answers.

I have an 8 port Oxford PCIe Serial card and can't seem to get it installed properly in Ubuntu 9.10. I'm thinking that, being a noob, I'm probably missing something easy.

I can see the card in LSPCI:

01:00.0 Serial controller: Oxford Semiconductor Ltd Device c308 (prog-if 02)
	Subsystem: Oxford Semiconductor Ltd Device c308
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ddffc000 (32-bit, non-prefetchable) [size=16K]
	Region 1: Memory at ddc00000 (32-bit, non-prefetchable) [size=2M]
	Region 2: Memory at dda00000 (32-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [70] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=16
		Vector table: BAR=1 offset=001b3000
		PBA: BAR=1 offset=001b2000
	Capabilities: [100] Device Serial Number 00-03-00-11-11-e0-30-00
	Capabilities: [110] Power Budgeting <?>
	Kernel driver in use: serial

But, can't seem to do anything else with it...

Compiling the drivers that came with it doesn't seem to help - runs into errors about EXTRA_CFLAGS when I try to make the file... Help? :(:)

---

### Post by akan1979 on 2010-03-01
This should help you get around your issue.   I had the same card and found the answer on the following post.


[http://ubuntuforums.org/showthread.php?t=1354962](http://ubuntuforums.org/showthread.php?t=1354962)

Good luck!

---

### Post by LawnDart471 on 2010-03-03
Thanks! That worked - I can see the ports now, and it "appears" the card is working, but I can't connect to any of my Cisco gear.

cat /proc/tty/driver/serial
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:86 rx:2001 RTS|DTR
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
2: uart:16C950/954 mmio:0xDDFFDC00 irq:16 tx:159 rx:0 RTS|DTR|RI
3: uart:16C950/954 mmio:0xDDFFDE00 irq:16 tx:37 rx:0 RTS|DTR|RI
4: uart:16C950/954 mmio:0xDDFFD000 irq:16 tx:32 rx:0 RTS|DTR|RI
5: uart:16C950/954 mmio:0xDDFFD200 irq:16 tx:24 rx:0 CTS|DSR|RI
6: uart:16C950/954 mmio:0xDDFFD400 irq:16 tx:24 rx:0 RI
7: uart:16C950/954 mmio:0xDDFFD600 irq:16 tx:24 rx:0 RI
8: uart:16C950/954 mmio:0xDDFFD800 irq:16 tx:24 rx:0 RI
9: uart:16C950/954 mmio:0xDDFFDA00 irq:16 tx:24 rx:0 RI

setserial -agv /dev/ttyS*
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS1, Line 1, UART: 16550A, Port: 0x02f8, IRQ: 3
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS2, Line 2, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS3, Line 3, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS4, Line 4, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS5, Line 5, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS6, Line 6, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS7, Line 7, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS8, Line 8, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

/dev/ttyS9, Line 9, UART: 16950/954, Port: 0x0000, IRQ: 16
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test


So, I'm closer, but not quite there... By default, the Baud_base setting was high - like 400000, but I was able to reset with setserial. Just wish I could get them communicating correctly. Trying to use Minicom with a Cisco serial/RJ45 rollover cable isn't working. If I use it in ttyS0, it works fine - same settings.

---

### Post by LawnDart471 on 2010-03-04
Okay - I've discovered something interesting that may or may not be causing my issue. Playing around with the serial ports in minicom and gtkterm, I discovered that there appears to be a Ring Indicator signal (RI) on all ports of the 8 port serial card.

Even with all cables unplugged and the card re-seated in the PCIe slot, it believes there's a signal there.

sudo cat /proc/tty/driver/serial
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
2: uart:16C950/954 mmio:0xDDFFDC00 irq:16 tx:24 rx:0 **RI**
3: uart:16C950/954 mmio:0xDDFFDE00 irq:16 tx:24 rx:0 **RI**
4: uart:16C950/954 mmio:0xDDFFD000 irq:16 tx:24 rx:0 **RI**
5: uart:16C950/954 mmio:0xDDFFD200 irq:16 tx:24 rx:0 **RI**
6: uart:16C950/954 mmio:0xDDFFD400 irq:16 tx:24 rx:0 **RI**
7: uart:16C950/954 mmio:0xDDFFD600 irq:16 tx:24 rx:0 **RI**
8: uart:16C950/954 mmio:0xDDFFD800 irq:16 tx:24 rx:0 **RI**
9: uart:16C950/954 mmio:0xDDFFDA00 irq:16 tx:24 rx:0 **RI**

When I plug in my Cisco console cable, the RI does not go away, and I think it may be interfering with communication to the port. I'm hoping that someone with more experience in this area can help me out. Is there some configuration I can perform to stop this behavior or do I just have a bad piece of hardware?

---

