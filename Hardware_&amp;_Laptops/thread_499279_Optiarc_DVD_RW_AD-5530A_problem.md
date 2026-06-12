---
title: "Optiarc DVD RW AD-5530A problem"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by MrBordello on 2007-07-12
Hi everyone!
since a week i own myself a [Gigabyte W551N Laptop]("http://www.gigabyte.com.tw/Products/Notebook/Products_Spec.aspx?ProductID=2190"). Ubuntu Feisty works almost perfect on it :)
BUT: there are some problems with the DVD-writer ([Sony? Optiarc DVD RW AD-5530A]("http://www.sonynec-optiarc.eu/en/exhibits/slim-line-drives/ad-5540a.html")). Writing of CD-R's works, but only at 4x-speed. DVDs get written too, but the medium is unreadable afterwards... After some searching i found this: [Bug #110636]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110636")
the guys there say it'll never be fixed! Is that true? Or is it something else? Please, help!

Output of hdparm -i /dev/sr0:
```
 Model=Optiarc DVD RW AD-5530A                 , FwRev=AX32    , SerialNo=30644770 1019599Q111
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode
```
no buffer :(

no problems here hdparm -i /dev/sda:
```
 Model=SAMSUNG HM120JI                         , FwRev=YF100-13, SerialNo=S0YYJ10P220573      
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode
```

---

