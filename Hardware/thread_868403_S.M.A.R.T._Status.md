---
title: "S.M.A.R.T. Status"
date: 2008-07-23
forum: Hardware
---

### Post by quantumstitch on 2008-07-23
I am looking for information more than anything else. I rebooted my machine a while back and as it was posting I got a 'bad' S.M.A.R.T. status message for IDE Master Channel 3. I am not sure if this message means anything because both my Seagate HDD are SATA. I have an IDE DVD burner that shows no signs of problems.

My motherboard has 6 SATA connections and one IDE connection. I haven't changed the ribbon cable for the DVD drive, nor the SATA cables for the hard drives. Can someone explain this message? Can I reset something to get rid of it, if it isn't really bad? 

Here's the output of hdparm -i if that helps,

```

root@daphne:~# hdparm -i /dev/sda

/dev/sda:

 Model=ST3500630AS                             , FwRev=3.AAK   , SerialNo=            6QG0Q7ZX
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

root@daphne:~# hdparm -i /dev/sdb

/dev/sdb:

 Model=ST3500630AS                             , FwRev=3.AAK   , SerialNo=            6QG0KSX8
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

I suppose I could turn S.M.A.R.T. off in the bios, but that seems unnecessary.

---

### Post by quantumstitch on 2008-07-23
Here's some more info...I used smartmontools to check the status of my drives. One is failing according to to smartctl. Can I fix this by reformatting?

```

root@daphne:/etc# smartctl -H /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
Failed Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   001   001   036    Pre-fail  Always   FAILING_NOW 35274

```

I have been using the drive for 2 weeks without problems.

---

### Post by Dark_Stang on 2008-07-23
Backup your stuff and replace the drive. If it's under warranty get it warrantied.

---

