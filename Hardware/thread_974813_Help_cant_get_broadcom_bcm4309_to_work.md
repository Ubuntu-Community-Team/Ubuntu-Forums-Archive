---
title: "Help cant get broadcom bcm4309 to work"
date: 2008-11-07
forum: Hardware
---

### Post by tontaloj on 2008-11-07
Hello,

I am new to Ubuntu and i just installed ubuntu8.4 on my Dell Inspiron 5100 laptop the other day and i can't seem to get the wifi to work...
I have read a few threads regarding this but nobody seems to get to the point. much help would be grateful. 

Here is the lspci -vv of the card is this helps 


02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
	Subsystem: Dell Truemobile 1400
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME+


thanks

J

---

### Post by phidia on 2008-11-07
Have you looked at the guide [here]("http://ubuntuforums.org/showthread.php?t=870086&highlight=BCM4309")?

---

### Post by tontaloj on 2008-11-07
it worked this time

had to compile from source.

thanks a lot

j

---

