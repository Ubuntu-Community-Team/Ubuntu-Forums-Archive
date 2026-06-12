---
title: "Graphical interference"
date: 2013-04-11
forum: Hardware
---

### Post by Olle/Nicki on 2013-04-11
I have installed Ubuntu Studio 12.04 and everything worked out of the box.
But there is a minor but irretating problem: When looking at a mail, Firefox or this site, some letters are not black. They are blue or green.
I have tryed to change the screen setting but no succes. 

Here is the output of lspci -v relative to graphic:

```
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 2130
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbfe0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at e000 [size=256]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon
```

Is it possible to fix this?

---

