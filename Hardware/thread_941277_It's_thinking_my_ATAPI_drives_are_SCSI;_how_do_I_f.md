---
title: "It's thinking my ATAPI drives are SCSI; how do I fix this? (possibly drivers)"
date: 2008-10-07
forum: Hardware
---

### Post by SlaughterDog on 2008-10-07
Ubuntu is saying my optical drives are connected via SCSI, but indeed, they are connected via PATA. The controller is a J-Micron JMB 363.

In Windows, I had to download 'basic drivers' from the J-Micron site to get it to not emulate SCSI. Their site says it's natively Linux compatable. 

In Windows, the problems it was causing was more obvious, such as not being able to write to discs at all.

In Linux, I can write to discs, but when reading, it's quite slow. I had 2 CD burners, and one read at 52x but the other, much slower (notable when ripping CDs). I just replaced the one that was working fast with a DVD writer (I replaced that one because it was the older of the two), with the hopes that the new one would rip at full speed, but it does not. 

I'd appreciate any help I can get.

This is something I saw on similar thread, so I'll provide this info here too.

```
todd@computer:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=SONY    CD-RW  CRX320EE                 , FwRev=RYK4    , SerialNo=2006070800050450    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

todd@computer:~$ hdparm -i /dev/scd1

/dev/scd1:

 Model=Optiarc DVD RW AD-7200A                 , FwRev=1.06    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no

 * signifies the current active mode

```

---

### Post by cariboo on 2008-10-08
Classifying CDrom drives as scci is normal for Linux. The drivers are included with the kernel. Burn speed depends on the quality of your media. I always burn at medium to low speed to get good quality burns. In Windows I burn at the slowest speed possible with the same model burner because I seem to burn more coaster in windows than I do in Linux.

Jim

---

### Post by SlaughterDog on 2009-01-26
Aye yie yie; I bought a PATA to SATA adapter (cost $21 with shipping) figuring it would solve the problem; I thought the problem with lack of read speed only applied to the drives hooked up to the PATA controller. So it is working fine, the drive hooked up to the SATA plug now, but you know what? It's still going at slow speeds! How can I get this sucker to rip faster? I think I'll put in my old drive for now but I want to get the other ones working right, too!

Edit: Jeeze, I put in the old one that used to rip at 52X, and now, 18X is the max. What gives?

---

