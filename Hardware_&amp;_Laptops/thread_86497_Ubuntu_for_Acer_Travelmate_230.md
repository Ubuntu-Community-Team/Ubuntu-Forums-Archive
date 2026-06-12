---
title: "Ubuntu for Acer Travelmate 230?"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by SuperDiscoMachine V.5.7-3 on 2005-11-05
Hi,

A friend recommended I switch to Ubuntu on my Acer Travelmate 230 laptop, however, I don't know as much about computers as him and parts, notably the graphics card and CD-RW/DVD drive don't work now and I'm not sure how to install them (the Acer site only has drivers for XP and Win2000). They say the parts are...

VGA Intel Montara-GML VGA Driver 6.13.01.3460

but it doesn't say what the CD drive is ([http://support.acer-euro.com/drivers/notebook/tm_230.html)](http://support.acer-euro.com/drivers/notebook/tm_230.html)). Any ideas on what to do? Run an external monitor due to problems with laptop screen so need the driver, however, I'm a complete novice :).

Thanks loads for your help!

---

### Post by ubuntu-tester on 2005-11-05
Hi you've to gather information about your hardware ...

as user root in a terminal do:

lspci -vv


You get Information like this ...

--------------------------------------------------------------------------------------------------
00:02.0 VGA compatible controller: Intel Corp. 82845G/GL [Brookdale-G] Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
	Subsystem: Unknown device 17c0:2056
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66Mhz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
-----------------------------------------------------------------------------------------------------

with this Information users can help a bit more ...

take a look at 

[http://liw.iki.fi/liw/texts/acer-travelmate-230xc](http://liw.iki.fi/liw/texts/acer-travelmate-230xc)
[http://rffr.de/tm230xc.php](http://rffr.de/tm230xc.php)
[www.di.unipi.it/~scordino/linux.html](www.di.unipi.it/~scordino/linux.html)

hope this helps ...

---

