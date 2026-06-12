---
title: "Toshiba Satellite L500 brightness hotkeys dead"
date: 2010-05-01
forum: Hardware
---

### Post by reinderien on 2010-05-01
Hi there. My brightness hotkeys (function+F6 and function+F7) don't work. Through some trial and error, I can manually change the brightness with:

echo -n 30 > /proc/acpi/video/GFX0/DD04/brightness

Obviously, this isn't ideal.

```
uname -a
Linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

``````
lspci
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f2100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

The brightness panel applet shows a red symbol and doesn't work. Any ideas on how to fix this? Thanks...

---

### Post by aoia456kl24 on 2010-06-27
I have the same problem - any thoughts?

John

---

### Post by S.R on 2010-06-28
You can try [http://sourceforge.net/projects/fnfx/](http://sourceforge.net/projects/fnfx/) ... It may or  may not work with your Toshiba model.

---

