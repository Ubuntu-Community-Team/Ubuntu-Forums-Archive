---
title: "High IO WAIT"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by berryman77 on 2005-04-25
I'm getting very high IO WAIT when doing disk intensive actions like untarring a file.  It's maxing out my CPU (Pentium M 1.6) and it seems unnecessary.  I've tried to configure the drive with hdparm.  My drive information is below.  I'm using Ubuntu 5.04.  Any idea what may be causing this or how i can correct it?

```
/dev/hda:

 Model=TOSHIBA MK6025GAS, FwRev=KA200K, SerialNo=15EL2517S
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode
```

---

