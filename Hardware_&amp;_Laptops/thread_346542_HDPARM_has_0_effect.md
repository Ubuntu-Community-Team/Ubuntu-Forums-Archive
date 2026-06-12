---
title: "HDPARM has 0 effect"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by dday376 on 2007-01-25
I've been reading on several posts about the benefits of HDPARM, and I'm wondering if I'm doing something wrong or if my hardware simply does not respond to the settings.  I configured /dev/hda with the following in hdparm.conf:

> 
/dev/hda {
       mult_sect_io = 16
       dma = on
       interrupt_unmask = on
       io32_support = 1
       transfer_mode = 69
}


which I originally tested in single-user mode as:

> hdparm -m16 -d1 -u1 -c1 -X69 /dev/hda

Test results were consistently around 23.5 MB/sec on buffered disk reads in single-user mode regardless of the settings I applied.

hdparm -i /dev/hda reports the following:

> dday@toth:~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHT2060AT, FwRev=009B, SerialNo=NN3LT4115S4E
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

I've noted that my BOIS indicates that MultiSector 16 and 32-Bit IO are enabled, even though hdparm indicates otherwise.  Anybody have a clue?  I have an HP Pavilion ze4805us.

Thanks!
- DDay376

---

### Post by K.Mandla on 2007-01-26
Don't feel bad. I've used those exact settings (or ones very close to those) and gotten no improvement on my transfer rates and boot times either.

In fact, sometimes I did better with the default (almost-all-off) settings than I did after using hdparm.

For my nickel, hdparm might have been useful four or five years ago, but nowadays it's not much to brag about. Perhaps if you have the right hardware, it'll make a difference.

---

### Post by dday376 on 2007-01-26
> **K.Mandla said:**
> Don't feel bad. I've used those exact settings (or ones very close to those) and gotten no improvement on my transfer rates and boot times either.

In fact, sometimes I did better with the default (almost-all-off) settings than I did after using hdparm.

For my nickel, hdparm might have been useful four or five years ago, but nowadays it's not much to brag about. Perhaps if you have the right hardware, it'll make a difference.

Thanks, K.Mandl.  I was suspecting that might be the case, but I can't find anything that explicitly states hdparm may have no effect on new hardware or certain types of laptops, etc.

- DDay376

---

