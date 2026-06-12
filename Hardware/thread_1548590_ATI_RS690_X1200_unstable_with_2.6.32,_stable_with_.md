---
title: "ATI RS690 X1200: unstable with 2.6.32, stable with 2.6.31"
date: 2010-08-08
forum: Hardware
---

### Post by sanderj on 2010-08-08
Hi,

My onboard VGA (ATI Technologies Inc RS690 [Radeon X1200 Series]) is unstable with kernel 2.6.32. It's OK with 2.6.31.

Symptons with kernels 2.6.32: after going into screen saver mode (a blank screen), I cannot get the system/screen back in a normal state: I can't get a screen at all, or the screen keeps flashing/scrolling, or I can type my password but then nothing happens and the system locks up (even pressing NumLock does not result in the LED turning on).
As the good old CTRL-ALT-BACKSPACE is gone nowadays, I have to press the reset button.

So my 'workaround': always boot in 2.6.31.

Any hints, tips or advice on this problem?

Thanks.

```

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
	Subsystem: ASUSTeK Computer Inc. Device 826d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f8000000 (64-bit, prefetchable) [size=64M]
	Region 2: Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at de00 [size=256]
	Region 5: Memory at fdc00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel modules: radeon

sander@athlon64:~$ uname -a
Linux athlon64 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
sander@athlon64:~$ 


```

---

