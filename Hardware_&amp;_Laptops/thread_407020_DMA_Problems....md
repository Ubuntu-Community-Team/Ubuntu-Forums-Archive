---
title: "DMA Problems..."
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by djseto on 2007-04-11
I have just spent the last 4 hours trying to get DMA to work on CDROM/DVD Drive. I have just about gone crazy. I read the Ubuntu Guide: [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

but that didnt help. When I do a "sudo hdparm -i /dev/cdrom", I get: 

-----------------------------------------------------------------------------
Model=DVDRW DRW-5S163, FwRev=YSG5, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 sdma? mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode
-----------------------------------------------------------------------------

as you can see, there is no asterisk to indicated the current active mode, however, when I type "sudo hdparm -d1 /dev/cdrom", I get:
-----------------------------------------------------------------------------
/dev/cdrom:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
-----------------------------------------------------------------------------

I am running on 2.6.17-11.  I have 1 IDE CD/DVD drive and 2 SATA drives. I have googled this to death. PLEASE PLEASE HELP.

---

### Post by coolclassic on 2007-04-11
When using the command "sudo hdparm -d1 /dev/cdrom" you are switching on dma, when you reboot this setting is lost. In the link you gave it tells you to edit the fstab file so dma is switched on at boot.

---

### Post by djseto on 2007-04-12
I am new to linux, so im not sure what you mean by fstab file, but if you are referring to the instructions to add the code:

dev/hdc {
dma = on
}

 to the hdparm.conf, I tried that and it still doesnt work. When I try to play audio from a CD, it sounds like garbage. If I try to rip CD's to Mp3, FLAC, etc., it sounds equally as bad, but if I play back mp3 files that were not ripped on the machine, everything sounds fine.

---

