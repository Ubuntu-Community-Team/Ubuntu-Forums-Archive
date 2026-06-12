---
title: "Problems with lpt (/dev/lp0)"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by Phrack on 2005-03-26
Hi

I got some problems with my lpt port (printer port). I have a Microtek SlimScan C6 scanner and an Epson Stylus Color 440 printer. Before I use Ubuntu, I had Mandrake  :-# in this pc and printer (but not scanner) works perfectly (using cups). Now, I tried with cups, lsmod, bios configuration and i got nothing with. Someone can tell me something to play around? thanks.

pd:

> $ dmesg | grep parport
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).

> $ lsmod | grep parport
parport_pc             34752  1
parport                40712  2 parport_pc,lp


---

