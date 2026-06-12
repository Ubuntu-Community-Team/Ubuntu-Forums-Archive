---
title: "DMA/33 being forced when it should be DMA/100"
date: 2008-05-04
forum: Hardware
---

### Post by grazzt on 2008-05-04
dmesg states the following:

```

[   30.584506] ata6.00: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
[   30.584521] ata6.00: limited to UDMA/33 due to 40-wire cable
[   30.600429] ata6.00: configured for UDMA/33

```

This is wrong, it is *not* a 40 wire cable, even windows (sigh) detects it as udma/100.

hdparm -I states the following:

```

	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns

```

IDE Chipset is Nforce3.

Ive tried irqpool kernel option, didnt help.

Any ideas?  DMA/33 sucks. :(

---

### Post by grazzt on 2008-05-04
I switched to the -rt kernel, and:

```

[   26.907349] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   26.908268] hdc: UDMA/100 mode selected

```

and

```

	R/W multiple sector transfer: Max = 16	Current = 0
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns

```

so the default kernel has some problems with its ide-scsi emulation or whatever detecting the correct DMA mode.. oh well.

---

