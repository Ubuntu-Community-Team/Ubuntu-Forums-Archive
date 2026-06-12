---
title: "Dell Latitude D610, 915GM, Intrepid - Max resolution a bobo 1024x768"
date: 2009-03-02
forum: Hardware
---

### Post by RgnKjnVA on 2009-03-02
I just want 1280x1024. I've updated intel drivers and tried resetting xorg.conf though it doesn't seem to make a bit of difference what is in that file. I have read a few other threads and it seems 915resolution isn't an option anymore, I don't find it in Synaptic. Anyone know if it will force the issue though since whatever is supposed to 'just work' in Intrepid doesn't? Any assistance greatly appreciated.

```
laptop:~$ sudo lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
	Subsystem: Dell Device [1028:0182]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
	Subsystem: Dell Device [1028:0182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ec38 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
	Subsystem: Dell Device [1028:0182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-



```


```
laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1024x768       60.0*+   50.0  
   800x600        60.3     56.2  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

```

---

### Post by 12261980 on 2009-03-03
Yeah, I spent good two weeks on this exact issue, and couldn't solve it. Anyone?

---

### Post by medic8ted on 2009-03-06
same problem

---

