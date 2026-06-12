---
title: "X58 no PATA support"
date: 2009-06-17
forum: Hardware
---

### Post by djamu on 2009-06-17
Ubuntu kernel doesn't load driver / module for Pata interface 

lscpi -v shows 
```

.....
03:00.1 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller (rev a0) (prog-if 85 [Master SecO PriO])
	Subsystem: ASRock Incorporation Device 0415
	Flags: fast devsel, IRQ 17
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Expansion ROM at f3ff0000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 3
	Capabilities: [70] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [90] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [130] Device Serial Number 00-8f-13-ff-ff-39-06-00
.....

```

does anyone know which driver it's supposed to use ?

---

### Post by Monker1980 on 2009-10-05
Did you ever get to the bottom of this, as I have the same issue on my new ASRock X58 Supercomputer board.

---

