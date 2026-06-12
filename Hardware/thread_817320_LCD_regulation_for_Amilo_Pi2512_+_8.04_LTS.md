---
title: "LCD regulation for Amilo Pi2512 + 8.04 LTS"
date: 2008-06-03
forum: Hardware
---

### Post by zipeppe on 2008-06-03
Hi guys,

a fresh installation of 8.04 LTS on a Fujitsu-Siemens Amilo Pi2512 using wubi installer: Amazing, less than 30' to get everything working!

:KS

One problem I noticed, even after the last upgrade: the LCD display is darker then in Windows, and I cannot regulate the brightness with Fn + F7.

Other Fn combinations work (as Fn + F5/F6 for volume setting), but no way to make the LCD panel more readible.  Also during the boot (I mean in the buffer mode vga=773) all the characters appear grey over a dark background, and it looks as a very low contrast.

This is the output from **lspci -v** command:


```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Fujitsu Siemens Computers Unknown device 1108
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Unknown device 1108
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+


```

Any idea to fix this?
[Here]("http://www.notebook-pcs.com/1722.html") some hardware specs

---

### Post by zipeppe on 2008-07-08
up

---

### Post by robang on 2008-11-10
Hi zipeppe, I hope you will read this post.
I would like to buy an Amilo pi2512 could you send me a lspci -vv? 
Could tell me which peripherals work and those do not?
Thank you very much,
Roberto :)

---

